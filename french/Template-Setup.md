> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="template-setup"></a>
# Configuration du modèle

**Référence du didacticiel :** [Regarder sur YouTube](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
(*Cliquez sur les horodatages ci-dessous pour accéder à des moments spécifiques de la vidéo*)

---

<a id="overview"></a>
## Aperçu

Les modèles dans **Joomla Component Builder (JCB)** sont plus que des extraits pratiques : ce sont des structures de vue modulaires et réutilisables qui enveloppent la couche de présentation de votre composant. Ils fournissent le squelette de haut niveau qui restitue les données pour les **vues de site** et les **vues d'administrateur personnalisées**, reflétant l'approche de création de modèles MVC de Joomla tout en restant entièrement modifiables.

Utilisez des modèles pour :

1. Coordonnez le HTML et le PHP qui enveloppent chaque vue.
2. Déléguez le balisage répété à des mises en page ou même à d'autres modèles.
3. Conservez la logique métier dans les modèles/contrôleurs tout en laissant les modèles se concentrer sur la présentation.
4. Partagez des blocs de construction d'interface utilisateur cohérents entre les composants ou les projets.

Dans ce tutoriel, nous aborderons :

1. Comprendre ce que sont les modèles JCB et pourquoi ils sont importants
2. Création de nouveaux modèles
3. Copie et modification de modèles existants
4. Gestion des chaînes de langue
5. Ajout de scripts personnalisés et de JavaScript
6. Comprendre comment les modèles s'intègrent aux vues du site
7. Synchronisation des modèles avec les référentiels pour une réutilisation collaborative

---

<a id="what-are-jcb-templates"></a>
## Que sont les modèles JCB ?

Les modèles JCB agissent comme des **enveloppeurs modulaires** autour de la sortie de votre composant. Dans un modèle, vous pouvez :

* Incluez d'autres modèles pour imbriquer des structures plus complexes.
* Mises en page de rendu (`JLayoutHelper::render()`) pour réutiliser des fragments.
* Mélangez la logique PHP et le HTML en toute sécurité, tout comme les modèles natifs de Joomla.

Étant donné que les modèles sont chargés via `$this->loadTemplate('name');`, ils ont un accès complet à l'objet de vue et à toutes les méthodes d'assistance que vous exposez. Cette parité avec l'approche par défaut de Joomla signifie que tout développeur déjà familier avec les modèles Joomla peut s'adapter rapidement au flux de travail de JCB.

---

<a id="why-use-templates-in-jcb"></a>
## Pourquoi utiliser des modèles dans JCB ?

Les modèles vous permettent de séparer clairement les préoccupations :

* **Cohérence :** réutilisez le même wrapper structurel sur plusieurs vues pour l'alignement visuel.
* **Maintenabilité :** mettez à jour un modèle et actualisez instantanément sa présentation partout où il est chargé.
* **Extensibilité :** remplacez ou étendez les modèles par projet, comme vous le feriez avec les remplacements de modèles principaux de Joomla.
* **Composabilité :** imbriquez les mises en page, appelez la logique d'assistance ou incluez d'autres modèles pour les interfaces utilisateur complexes.

Les modèles sont particulièrement utiles lorsque vous :

* Construire une suite de composants qui doivent partager le même système de conception.
* Maintenir des tableaux de bord d'administration personnalisés nécessitant des panneaux ou des grilles reproductibles.
* Création d'expériences frontend qui mélangent plusieurs fragments dynamiques sur une seule page.

---

<a id="managing-templates-in-the-jcb-interface"></a>
## Gestion des modèles dans l'interface JCB

Les modèles sont gérés directement à partir de l'onglet **Modèles** dans l'interface graphique de JCB. Ici, vous pouvez :

1. Cliquez sur **Init** pour vous connecter à un référentiel.
2. Choisissez le référentiel qui stocke les modèles réutilisables.
3. Sélectionnez des modèles individuels à **importer**, **réinitialiser** ou **pousser** vers la source.

Ce flux de travail basé sur le référentiel maintient les équipes synchronisées. Vous pouvez créer une bibliothèque officielle, gérer une collection privée ou contribuer à des mises à jour en amont, le tout sans quitter l'interface.

---

<a id="creating-templates"></a>
## Création de modèles

[00:00:00](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Dans le didacticiel précédent, nous avons expliqué comment configurer des modèles et des mises en page pour une **vue de site**. Dans une vue de site typique, comme `preacherpanel`, `preachersmall` ou `preacherbox`, vous trouverez des modèles chargés pour définir la façon dont les données sont affichées.

Pour les consulter ou les modifier, rendez-vous sur :
**JCB → Modèles**

Ici, tous les modèles disponibles sont répertoriés, chacun correspondant à une mise en page utilisée dans une ou plusieurs vues du site.

---

<a id="creating-or-copying-templates"></a>
## Création ou copie de modèles

[00:00:27](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m27s)

Pour créer un nouveau modèle :

1. Cliquez sur **Nouveau** dans la zone Modèles JCB.

* Vous pouvez également en copier un existant en le sélectionnant et en utilisant la fonction **Batch → Copier**.
   * Cliquez sur **Traiter** pour terminer la copie.

[00:00:49](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m49s)

Ouvrez le modèle **Preacher Panel** (utilisé dans l'exemple du didacticiel).
Cette zone contient la **vue HTML** de votre mise en page. Si vous préférez utiliser PHP, passez en mode éditeur PHP. Vous pouvez basculer d'avant en arrière selon vos besoins.

**Conseil :** Utilisez des espaces réservés de texte (`{placeholder}`) dans votre modèle pour rendre le contenu traduisible et remplacé dynamiquement lors du rendu.

---

<a id="language-strings"></a>
## Chaînes de langue

[00:01:20](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m20s)

JCB ajoute automatiquement vos chaînes de texte au **fichier de langue** de votre composant.
Par défaut, il gère les entrées **British English (en-GB)**.

Si vous avez besoin de langues supplémentaires :

* Suivez l'approche standard de Joomla pour ajouter des remplacements de langue.
* Copiez le fichier anglais dans votre langue cible (par exemple, `fr-FR.com_yourcomponent.ini`).
* Traduisez chaque ligne en conséquence.

[00:01:44](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m44s)

<a id="layout-snippets"></a>
### Extraits de mise en page

Dans les **extraits de code de mise en page**, vous pouvez :

* Intégrez des **mises en page** dans les modèles.
* Imbriquer **les modèles dans les modèles**.
* Référencez les mises en page existantes pour un code modulaire et maintenable.

Ce comportement est cohérent avec la façon dont les mises en page et les modèles sont gérés dans les vues du site Joomla.

---

<a id="adding-custom-script-or-code-to-a-template"></a>
## Ajout d'un script ou d'un code personnalisé à un modèle

[00:02:13](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m13s)

Chaque modèle comprend une **Snippet Box**, qui vous permet d'insérer rapidement des scripts ou une logique en ligne.
Par exemple, vous pouvez ajouter un petit bloc PHP ou JavaScript pertinent pour l'affichage des données de votre modèle.

L'exemple de **Preacher Panel** dans la vidéo montre comment un script en ligne peut améliorer l'interactivité d'une vue.

**Bonne pratique :** Conservez la logique métier dans le modèle ou le contrôleur de votre vue et utilisez des extraits de code uniquement pour les comportements mineurs de l'interface utilisateur.

---

<a id="adding-javascript-to-a-template"></a>
## Ajout de JavaScript à un modèle

[00:02:46](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s)

Dans l'onglet **Détails** de votre modèle, vous trouverez une note sur l'ajout de JavaScript.

Pour inclure JS :

1. Enveloppez votre code dans des balises `<script>`.
2. Il se chargera automatiquement sur la page frontale de votre composant.

[00:03:13](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m13s)

Vous avez toujours un accès complet à toutes les **valeurs globales du champ "ceci"**, ce qui signifie que votre JS peut interagir dynamiquement avec les données d'exécution de JCB.

[00:03:35](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m35s)

Les modèles utilisent les mêmes conventions de configuration que les **vues de site**, sauf qu'il ne s'agit que de **vues non autonomes**. Au lieu de cela, les modèles sont inclus **dans** une vue principale via la méthode `getTemplate()` de Joomla.

---

<a id="loading-templates-dynamically"></a>
## Chargement dynamique des modèles

[00:04:02](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m02s)

Pour charger un modèle depuis une vue :

```php
echo $this->loadTemplate('preacherpanel');
```

Cette méthode inclut le fichier modèle spécifié et le restitue avec toutes les variables disponibles.

[00:04:29](https://www.youtube.com/watch?v=khxKeeubhiY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m29s)

C'est ainsi que votre modèle devient partie intégrante de la vue principale des composants, garantissant que tous les scripts, extraits de code et traductions sont automatiquement intégrés.

---

<a id="summary"></a>
## Résumé

* Les modèles dans JCB sont des éléments de mise en page modulaires pouvant inclure HTML, PHP et JavaScript.
* Vous pouvez facilement **créer**, **copier** ou **étendre** des modèles à partir de l'interface JCB et les synchroniser via les importations/exportations du référentiel.
* Les chaînes de langue sont gérées automatiquement pour l'anglais mais peuvent être étendues.
* Des extraits de code et JS peuvent être ajoutés en toute sécurité pour la personnalisation de l'interface utilisateur.
* Les modèles sont liés aux vues principales via la méthode Joomla `loadTemplate()`.

---
