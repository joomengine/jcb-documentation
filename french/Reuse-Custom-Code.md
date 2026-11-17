> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="reusing-custom-code-in-joomla-component-builder-jcb"></a>
# Réutilisation de code personnalisé dans Joomla Component Builder (JCB)

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h00m00s)

Ce didacticiel montre comment réutiliser et gérer le **code PHP personnalisé** dans différentes parties de vos projets Joomla Component Builder (JCB). Il montre comment centraliser vos scripts, fonctions et assistants pour plus d'efficacité et de maintenabilité.

JCB comprend plusieurs fonctionnalités puissantes qui permettent de :

* Écrivez une fois des fonctions d'assistance génériques et utilisez-les sur plusieurs composants.
* Insérez dynamiquement des extraits de code réutilisables dans les modèles de composants.
* Conservez une logique personnalisée à partir d'un emplacement central au lieu de modifier plusieurs fichiers.

---

<a id="scenario-the-need-for-code-reuse"></a>
## Scénario : la nécessité de réutiliser le code

[00:00:33](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h00m33s)

Un développeur (Alex Dings) a posé une question sur le forum JCB :

> "J'ai plusieurs vues d'administration qui partagent du code générique, mais certaines vues nécessitent des variations spécifiques. Comment puis-je maintenir efficacement cette structure ?"

<a id="common-challenges"></a>
### Défis courants :

* Duplication des fonctions d'assistance PHP dans différentes vues d'administration.
* Mise à jour de plusieurs fichiers de composants chaque fois que la logique change.
* Gestion des fonctionnalités **génériques** et **spécifiques** dans plusieurs vues générées par JCB.

JCB résout ce problème grâce aux **blocs de code personnalisés** et aux **injections de classe d'assistance**.

---

<a id="setting-up-the-jcb-environment"></a>
## Configuration de l'environnement JCB

[00:01:12](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h01m12s)

Pour suivre, utilisez un environnement de test Joomla. Vous pouvez rapidement créer une **instance Joomla basée sur Docker** à des fins de test.

<a id="steps"></a>
### Étapes :

1. Extrayez une image Joomla Docker :

   ```bash
   docker pull joomla
   docker run -p 8080:80 joomla
   ```2. Accédez à Joomla à `http://localhost:8080`
3. Connectez-vous en tant qu'administrateur et accédez à :
   **Extensions → Installer → Web → Rechercher "JCB"**
4. Installez **Joomla Component Builder** à partir du répertoire d'extensions Joomla (JED).

[00:02:22](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h02m22s)

Initialisez l'[index du référentiel](./JCB-Packaging-Engine.md) et utilisez **Init** dans la vue Composants pour
importez les plans de démonstration fournis avec JCB. Ils fournissent des exemples concrets de la façon dont le code personnalisé est
structuré au sein de projets complets.

> **Conseil :** Cliquez toujours sur **Forcer la mise à jour locale** pour vous assurer que vos champs et votre structure JCB locaux sont à jour.

Une fois installé, vous pouvez explorer les composants internes de JCB et étudier ses **données de démonstration**.

---

<a id="understanding-custom-code-in-jcb"></a>
## Comprendre le code personnalisé dans JCB

[00:03:00](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h03m00s)

JCB inclut un **Custom Code Manager** sous :

> **Composant → Code personnalisé**

Cette zone permet de définir des blocs de code réutilisables qui sont injectés lors de la compilation. L'interface utilisateur étiquette désormais deux workflows complémentaires :

1. **JCB (manuel)** – Écrivez un extrait de code réutilisable une fois, injectez-le n'importe où avec `[CUSTOMCODE=...]` et transmettez éventuellement des arguments correspondant à `[[[arg0]]]`, `[[[arg1]]]`, etc. N'oubliez pas d'encoder les caractères réservés tels que `,` ou `+` (`&#44;`, `&#43;`) lors de l'envoi. comme arguments.
2. **Hash (automatisation)** – Entourez le code à l'intérieur d'un composant compilé de balises d'insertion ou de remplacement (par exemple `/***[INSERT<>123]***/`) afin que JCB puisse importer le bloc, suivre son emplacement et le réappliquer sur les versions futures.

Les deux types résident dans le même gestionnaire, vous pouvez donc mélanger une logique d'assistance réutilisable avec des remplacements sur disque sans perdre la relation avec leurs fichiers cibles.

---

<a id="example-1-using-the-getviewid-custom-code"></a>
## Exemple 1 : Utilisation du code personnalisé `getViewID()`

[00:03:40](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h03m40s)

Un bon exemple tiré des données de démonstration de JCB est la fonction **`getViewID()`**.

Cette fonction est créée sous la forme d'un extrait réutilisable dans **Code personnalisé** et est appliquée sur plusieurs **Vues d'administration**.

<a id="example-workflow"></a>
### Exemple de flux de travail :

1. Ouvrez **Code personnalisé → getViewID**
2. Observez où il est utilisé (par exemple, dans les vues d'administration).
3. L'extrait pourrait ressembler à :

   ```php
   public static function getViewID($view)
   {
       // Function logic
   }
   ```4. Dans votre vue administrateur, appelez la fonction comme :

   ```php
   $id = HelperClass::getViewID('myview');
   ```

[00:04:55](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h04m55s)

Si votre fonction inclut des variables telles que `vdm`, vous pouvez les rendre dynamiques à l'aide d'espaces réservés pour les arguments.

<a id="passing-arguments-to-custom-code"></a>
### Passer des arguments au code personnalisé

Vous pouvez remplacer des variables à l'aide de la **syntaxe d'espace réservé d'argument** :

```php
[[[[arg0]]]]
```

Ensuite, transmettez les arguments pendant l'utilisation :

* `arg0` → `value1`
* `arg1` → `value2`

Cela rend vos extraits de code plus flexibles dans différents contextes.

---

<a id="example-2-helper-function-reuse---getfilepath"></a>
## Exemple 2 : Réutilisation de fonctions d'assistance - `getFilePath()`

[00:05:55](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h05m55s)

La deuxième méthode de réutilisation du code consiste à ajouter des fonctions à vos **Classes d'assistance**.

Dans JCB, vous pouvez définir le code à ajouter automatiquement à :

* **Classe d'aide à l'administration**
* **Classe d'aide au site**
* **Les deux simultanément**

<a id="example"></a>
### Exemple:

La fonction `getFilePath()` peut être définie une fois et réutilisée dans plusieurs composants.

```php
public static function getFilePath($file)
{
    // Return the full path to a given file
}
```

[00:06:20](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h06m20s)

Chez JCB :

1. Ouvrez **Code personnalisé → PHP Helper (administrateur et site)**
2. Ajoutez-y votre fonction réutilisable.
3. JCB l'inclut automatiquement dans les deux classes d'assistance lors de la compilation.

> **Bonne pratique :** Utilisez l'option de classe d'assistance « Les deux » lorsqu'une fonction s'applique globalement.

Vous pourrez ultérieurement voir où chaque bloc de code personnalisé est utilisé au bas de sa page de détails.

---

<a id="managing-reuse-across-components"></a>
## Gestion de la réutilisation entre les composants

[00:07:45](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h07m45s)

Parce que les extraits de code personnalisés sont suivis de manière centralisée dans JCB :

* Vous pouvez facilement les modifier ou les mettre à jour une fois.
* Tous les composants qui utilisent l'extrait obtiendront le code mis à jour après la recompilation.

Ceci est particulièrement utile pour gérer les **bibliothèques partagées** de logique qui apparaissent dans plusieurs composants générés par JCB.

---

<a id="understanding-automation-and-ide-linked-code"></a>
## Comprendre l'automatisation et le code lié à l'IDE

[00:08:28](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h08m28s)

JCB distingue :

* **Code personnalisé de hachage (automatisé) :** Géré par JCB et inséré automatiquement dans des fichiers spécifiques (liés aux modifications de l'IDE).
* **Code personnalisé manuel :** Extraits autonomes créés pour être réutilisés dans différentes parties des composants.

<a id="key-differences"></a>
### Différences clés :

| Tapez | Objectif | Contrôle |
| -------------------- | ------------------------------------ | ----------------- |
| **Automatisé (hachage)** | Un fichier/un emplacement | Suivi par l'IDE |
| **Manuel (extrait)** | Utilisations multiples | Géré par le développeur |

> **Remarque :** Les deux utilisent le terme « code personnalisé », mais ont des objectifs distincts. Ne confondez pas les deux lors de la gestion des extraits.

---

<a id="summary"></a>
## Résumé

[00:09:25](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h09m25s)

**La réutilisation du code personnalisé** est l'un des outils les plus puissants permettant de gagner du temps dans Joomla Component Builder.
En structurant correctement votre logique réutilisable en utilisant :

* **Injections de classe Helper**, et
* **Extraits personnalisés manuels**,

vous pouvez considérablement améliorer l’efficacité et réduire les frais de maintenance.

---

<a id="key-takeaways"></a>
## Points clés à retenir

* Utilisez **Code personnalisé (manuel)** pour des extraits flexibles et multi-usages.
* Utilisez **Helper Class (Both)** pour une logique réutilisable partagée entre les zones d'administration et de site.
* Utilisez **Automated (Hash)** uniquement pour le code en ligne unique.
* Toujours **recompiler votre composant** après avoir mis à jour le code personnalisé pour appliquer les modifications.

---
