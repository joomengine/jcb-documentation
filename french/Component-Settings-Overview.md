> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="component-settings"></a>
# Paramètres des composants

> **Source vidéo :** [Paramètres des composants](https://www.youtube.com/watch?v=V2WkTjNFjvo&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
---

<a id="introduction"></a>
## Introduction

[00:00:00](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h00m00s)

Une fois que vous avez ajouté vos vues d'administration au composant, JCB fournit des zones de configuration supplémentaires appelées **Paramètres du composant**. C'est ici que vous gérez les **champs de configuration globaux**, les **menus d'administration personnalisés**, les **dossiers** et l'**intégration du compilateur**.

Les menus d'administration personnalisés contrôlent la structure des menus back-end, tandis que la zone **paramètres du composant** définit les options de configuration qui s'appliquent globalement à l'ensemble de votre composant.

> Si vous avez besoin d'un rappel sur tout ce qu'un composant regroupe, commencez par [Composants Joomla dans JCB](./Joomla-Components.md). Il décrit la manière dont ces paramètres s'intègrent dans le processus d'emballage plus large.

---

<a id="1-compiler-overview"></a>
## 1. Présentation du compilateur

[00:00:51](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h00m51s)

JCB inclut une **Vue du compilateur** interne, qui existe en dehors de la structure des composants standard.
Cette vue du compilateur nécessite :

*Un **modèle**
* Un **contrôleur**
* Une **vue**
* Fichiers d'aide et de script

À l'intérieur de l'infrastructure JCB, il existe un dossier appelé **custom**. C'est ici que vous placez les fichiers et dossiers qui doivent être inclus dans la compilation de votre composant.

> **Conseil :** Ne supprimez pas le contenu par défaut du dossier `/custom`. JCB utilise ces fichiers automatiquement lors de la compilation en fonction de votre configuration.

[00:02:02](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h02m02s)
Le compilateur possède ses propres **fichiers par défaut** et une **structure vide** qui peut être étendue avec une logique personnalisée, y compris des intégrations de contrôleurs et de modèles.

---

<a id="2-adding-custom-files-and-folders"></a>
## 2. Ajout de fichiers et de dossiers personnalisés

[00:03:50](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h03m50s)

Les fichiers et dossiers personnalisés vous permettent d'importer du contenu créé manuellement dans votre composant au moment de la compilation.

**Mesures:**

1. Placez les fichiers que vous souhaitez inclure dans le dossier `custom`.
2. Spécifiez les chemins de fichiers dans les paramètres du composant.
3. Renommez-les correctement en utilisant la convention de dénomination correcte.
4. JCB :

* Créez les dossiers nécessaires dans le composant compilé.
   * Déplacez vos fichiers dans ces dossiers.

[00:04:16](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h04m16s)
Le processus garantit que la création du dossier a lieu avant la copie du fichier, préservant ainsi l'intégrité structurelle.

---

<a id="3-creating-custom-admin-views"></a>
## 3. Création de vues d'administration personnalisées

[00:04:54](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h04m54s)

Utilisez la section **Menus d'administration personnalisés** pour définir de nouveaux éléments de menu backend non générés automatiquement par JCB.

**Exemple de flux de travail :**

1. Créez un nouveau menu d'administration personnalisé nommé **"Compilateur"**.
2. Définissez le **nom de code** sur `compiler`.
3. Choisissez une **icône** appropriée.
4. Spécifiez son emplacement, par exemple "avant le composant".

[00:05:17](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h05m17s)
Vous pouvez configurer s'il apparaît comme :

* Un menu d'administration
* Un élément du tableau de bord
* Un sous-menu

> **Conseil de pro :** La vue du compilateur elle-même peut être incluse dans la construction via la fonctionnalité d'importation de fichiers/dossiers personnalisés.

---

<a id="4-configuring-global-settings-config-area"></a>
## 4. Configuration des paramètres globaux (zone de configuration)

[00:07:27](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h07m27s)

La **Zone de configuration** dans les paramètres du composant définit vos **champs de configuration globaux**, accessibles sous « Options » dans le menu du composant backend.

<a id="example-sermon-distributor-component"></a>
### Exemple : composant de distributeur de sermons

Dans la démo Sermon Distributor, la section de configuration comprend plusieurs **onglets et commutateurs**, tels que :

* **Minuterie d'enregistrement :** Automatise les enregistrements périodiques des enregistrements.
* **Contrôle de version :** Active ou désactive la gestion des versions et définit le nombre de versions à conserver.

[00:09:07](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h09m07s)

---

<a id="5-adding-contributors"></a>
## 5. Ajouter des contributeurs

[00:09:21](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h09m21s)

Dans les paramètres du composant, vous pouvez ajouter une section **Contributeurs** pour les crédits de développement.

* Ajoutez des champs de contributeur ou laissez les champs vides pour des entrées ultérieures.
* Contrôler la visibilité (backend/frontend).
* Définir automatiquement les autorisations.

Ceci est utile pour documenter qui a aidé à développer le composant.

---

<a id="6-including-uikit"></a>
## 6. Y compris UIkit

[00:10:33](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h10m33s)

Vous pouvez activer l'intégration **UIkit** directement dans les paramètres du composant.
Lorsqu'il est activé, UIkit est automatiquement inclus dans les vues d'administration et de site de votre composant.

---

<a id="7-adding-fields-to-config"></a>
## 7. Ajout de champs à la configuration

[00:11:06](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h11m06s)

Pour ajouter un nouveau champ à la configuration de votre composant :

1. Accédez à **Champs** dans JCB.
2. Créez un nouveau champ (mémorisez son **nom du système**).
3. Référencez-le dans l'onglet Config en utilisant ce même nom.

> **Convention :** Les champs regroupés sous un même nom d'onglet apparaîtront ensemble dans la même section de configuration.

Exemple : Les champs *Méthode de mise à jour Dropbox* du composant de démonstration définissent des paramètres tels que `local folder` et `download link`.

[00:12:56](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h12m56s)

---

<a id="8-spacer-hr-field"></a>
## 8. Champ RH Spacer

[00:13:24](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h13m24s)

Le champ **Spacer HR** est une fonctionnalité simple mais utile pour organiser vos mises en page de configuration.

* Ajoute des séparateurs visuels entre les groupes de champs.
* Utilise des incréments de dénomination automatiques pour éviter les conflits.
* Peut inclure des **valeurs par défaut** qui sont renseignées lors de l'installation.

> Les valeurs par défaut sont stockées dans la base de données et chargées automatiquement lors de l'installation des composants.

---

<a id="9-linking-config-tabs-to-site-views"></a>
## 9. Lier les onglets de configuration aux vues du site

[00:14:55](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h14m55s)

Si un nom d'**onglet de configuration** correspond à un **nom de vue frontale**, JCB les liera automatiquement.

<a id="example"></a>
### Exemple:

* Onglet Configuration : `preachers`
* Vue du site : `preachers`

Cela permet de remplacer les paramètres globaux dans des éléments de menu spécifiques, similaires aux paramètres d'article intégrés de Joomla.

[00:17:07](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h17m07s)

---

<a id="10-how-it-works-in-the-site-view"></a>
## 10. Comment cela fonctionne dans la vue du site

[00:19:57](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h19m57s)

Chaque vue de site possède un fichier **`default.xml`** correspondant qui définit les paramètres disponibles.
Lorsqu'un onglet de configuration correspond au nom de la vue du site, JCB ajoute automatiquement ces paramètres au XML.

Si quelque chose n'apparaît pas comme prévu, inspectez ce fichier dans votre modèle de vue de site.

---

<a id="11-quick-overview-of-site-view-creation"></a>
## 11. Aperçu rapide de la création de vues de site

[00:20:45](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h20m45s)

Lors de la création d'une vue de site :

* Si vous **réglez « Ajouter comme menu » sur Oui**, JCB générera automatiquement le fichier `default.xml`.
* Si défini sur **Non**, le fichier XML du menu n'existera pas.

La définition des onglets avec le même nom que votre vue garantit le mappage des champs et des configurations uniques pour chaque élément de menu.

---

<a id="12-using-parameters-in-code"></a>
## 12. Utilisation des paramètres dans le code

[00:21:50](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h21m50s)

Dans les fichiers de vue PHP de votre composant (`view.html.php`), les paramètres sont accessibles via les méthodes `get()` de Joomla.

```php
$params = $this->state->get('params');
$displayType = $params->get('preachers_display', 'list');
```

Cela récupère :

* Paramètres des menus
* Paramètres des composants
* Solutions de secours globales (si le menu est défini sur "Utiliser Global")

> **Important :** Les noms de champs dans la configuration doivent être **uniques**. Les noms réutilisés peuvent provoquer des conflits lors de la récupération des paramètres.

---

<a id="13-practical-example---display-modes"></a>
## 13. Exemple pratique - Modes d'affichage

[00:25:59](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h25m59s)

Dans l'exemple du distributeur de sermons :

* Si `preacher_display = 1` → afficher **Tableau**
* Si `preacher_display = 2` → afficher **Grille**
* Sinon → afficher la **Liste**

Ces valeurs sont gérées globalement et accessibles dynamiquement dans la vue frontale.

---

<a id="14-advanced-mysql-tweak"></a>
## 14. Avancé : ajustement de MySQL

[00:28:44](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h28m44s)

La fonctionnalité **MySQL Tweak** de JCB vous permet d'**exclure ou de modifier des données factices** lors de l'exportation.
Ceci est particulièrement utile si vous gérez **plusieurs versions** de la même extension à différents niveaux tarifaires.

Vous pouvez contrôler quelles données sont incluses lors de la compilation de chaque version.

---

<a id="conclusion"></a>
## Conclusion

[00:29:17](https://www.youtube.com/watch?v=V2WkTjNFjvo&t=00h29m17s)

Dans ce tutoriel, nous avons exploré :

* Menus d'administration personnalisés et inclusion du compilateur
* Ajout de fichiers et dossiers personnalisés
* Création et liaison des champs de configuration
* Gestion des paramètres globaux
* Utilisation de conventions pour lier les paramètres backend aux menus frontend

Comprendre ces **paramètres au niveau des composants** vous permet de créer des composants Joomla **puissants, flexibles** et **structurés de manière professionnelle**.

---
