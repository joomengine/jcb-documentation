> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="a-quick-demonstration-to-load-a-list-of-items-in-a-site-view"></a>
# Une démonstration rapide pour charger une liste d'éléments dans une vue de site

Ce didacticiel montre comment créer et configurer une **Vue de liste** dans Joomla Component Builder (JCB) à l'aide des méthodes **Dynamic GET** et **AJAX (FooTable)**. Il explique également comment intégrer la liste dans une vue de site, ajuster les modèles et gérer les champs de configuration - en suivant exactement le flux de travail de Joomla Component Builder.

> **Objectif :** Chargez une liste d'éléments (des sermons, dans ce cas) dans une vue de site Joomla sans filtres, avec contrôle de pagination et de mise en page.

---

<a id="overview"></a>
## Aperçu
Dans Joomla Component Builder, les **Vues du site** définissent ce que les utilisateurs voient sur le frontend. Vous pouvez utiliser des **requêtes GET dynamiques** pour extraire des données de vos tables de base de données et les afficher dans des listes, des grilles ou des tableaux.  
Ce didacticiel étend l'exemple de composant Sermon Distributor pour démontrer le chargement de **tous les sermons** dans une seule vue de site, avec des options d'affichage flexibles.

---

<a id="step-1-review-existing-site-views"></a>
## Étape 1 : Examiner les vues de site existantes  
[00:00:35](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h00m35s)

Commencez par examiner vos vues de site existantes dans JCB.  
Dans cet exemple, le composant Sermon Distributor comprend déjà plusieurs vues :

- Sermons  
- Prédicateurs  
- Série  
- Catégories  
-API

Pour ce didacticiel, nous modifierons la vue **Preachers**, car il s'agit d'une **requête de liste**, adaptée à la démonstration.

---

<a id="step-2-understand-the-two-list-building-methods"></a>
## Étape 2 : Comprendre les deux méthodes de création de liste  
[00:01:05](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h01m05s)

Il existe **deux approches principales** pour charger une liste d'éléments dans une vue de site :

1. **GET dynamique (méthode standard)**  
   - Construit directement au sein de JCB.  
   - Idéal pour les ensembles de données petits à moyens (~ 100 éléments par page).  
   - Utilise la pagination.

2. **AJAX (méthode avancée utilisant FooTable)**  
   - Charge de grands ensembles de données (jusqu'à 10 000 éléments).  
   - Utilise le chargement asynchrone via les points de terminaison JavaScript et JSON.  
   - Idéal pour les tableaux réactifs et modifiables.

> **Conseil :** Si votre ensemble de données dépasse ~100 enregistrements par page, préférez l'approche AJAX + FooTable pour de meilleures performances et une meilleure expérience utilisateur.

---

<a id="step-3-review-the-ajax-footable-example"></a>
## Étape 3 : Consultez l'exemple AJAX FooTable  
[00:02:35](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h02m35s)

FooTable charge dynamiquement les données dans un tableau HTML avec seulement un minimum de JavaScript :

- Une **URL pour les en-têtes de colonnes** (source JSON)  
- Une **URL pour les données de l'article** (point de terminaison JSON)

```html
<table id="sermons-table" class="footable"></table>
<script>
  $('#sermons-table').footable({
      "columns": "path/to/columns.json",
      "rows": "path/to/items.json"
  });
</script>
````

Cette méthode prend en charge :

* **Mises en page réactives**
* **Édition instantanée**
* **Pagination dans le tableau**

> ⚙️ Joomla propose également des bibliothèques de tables similaires, mais FooTable reste une solution fiable et légère qui s'intègre facilement à JCB.

---

<a id="step-4-build-a-dynamic-get-query"></a>
## Étape 4 : Créer une requête GET dynamique

[00:06:00](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h06m00s)

Accédez aux **GETs dynamiques** dans JCB.
Vous verrez les requêtes existantes, par exemple la récupération de sermons ou de prédicateurs. Chaque « requête de liste » récupère plusieurs enregistrements de la base de données.

Nous allons en créer un nouveau appelé **`Sermons All`**.

1. **Dupliquez** une requête Sermons GET existante.
2. Renommez-le en **`Sermons All`**.
3. Supprimez les filtres inutiles (comme `preacher_id`).
4. Conservez uniquement le filtre **niveau d'accès** pour de bonnes pratiques.

Cela garantit que tous les sermons sont chargés, en respectant les autorisations d'accès de Joomla.

---

<a id="-step-5-understanding-helper-routes"></a>
## 🔗 Étape 5 : Comprendre les itinéraires d'assistance

[00:08:01](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h08m01s)

JCB génère automatiquement des classes d'assistance (par exemple, `/helpers/route.php`) qui créent dynamiquement des URL frontales.
Chaque lien de liste ou d'élément utilise des assistants d'itinéraire tels que :

```php
SermondistributorHelperRoute::getSermonRoute($slug);
SermondistributorHelperRoute::getSeriesRoute($slug);
```

Ces méthodes statiques :

* Créez des URL optimisées pour le référencement basées sur le slug de l'article (`alias:id`).
* Ajoutez le `Itemid` correct pour le contexte du menu.
* Utilisez `JRoute::_()` pour convertir les URL selon les paramètres SEF de Joomla.

> **Remarque :** Vous avez rarement besoin de les modifier manuellement - JCB gère leur génération de manière dynamique.

---

<a id="step-6-create-the-site-view-all-sermons"></a>
## Étape 6 : Créer la vue du site « Tous les sermons »

[00:14:27](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h14m27s)

Maintenant que nous avons une requête fonctionnelle, créez une nouvelle **Vue du site** appelée **"Tous les sermons"** :

1. Dupliquez la vue du site **Preachers** ou **Sermons** existant.
2. Renommez-le en **Tous les sermons**.
3. Mettez à jour la source **Dynamic GET** vers `sermons_all`.
4. Mettez à jour les clés et références `params` de `preacher` vers `all`.
5. Ajustez les valeurs de contexte pour utiliser `sermon` pour les autorisations.
6. Supprimez les zones spécifiques au prédicateur (comme les compteurs d'accès ou les informations sur le prédicateur).

Cela garantit que la nouvelle vue représente proprement tous les sermons sans filtres.

---

<a id="step-7-adjust-templates-and-layouts"></a>
## Étape 7 : Ajuster les modèles et les mises en page

[00:19:08](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h19m08s)

Dans votre zone JCB **Modèles**, recherchez et mettez à jour les mises en page suivantes :

* `sermons_table`
* `sermons_grid`
* `sermons_list`

Au sein de chacun :

* Remplacez tout espace réservé `SView` par `all`.
* Mettre à jour les paramètres pour la description du sermon, la catégorie et les hits.

> **Conseil :** Si les paramètres ne sont pas encore définis dans la configuration du composant, ils reviendront à `0`, ce qui signifie aucun chargement de données. Vous résoudrez ce problème à l’étape suivante.

---

<a id="step-8-extend-component-configuration-fields"></a>
## Étape 8 : Étendre les champs de configuration des composants

[00:31:52](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h31m52s)

La configuration du composant définit les options d'affichage globales telles que :

* Style de liste (tableau/grille/liste)
* Afficher/Masquer la description, les hits, les téléchargements, etc.

Pour prendre en charge la nouvelle vue « Tous les sermons » :

1. Accédez à **Configuration des composants** dans JCB.
2. Dupliquez les champs « Prédicateur » pertinents.
3. Renommez chacun pour utiliser le préfixe `all_` (par exemple, `all_display`, `all_hits`, `all_description`).
4. Marquez-les comme **Global**.
5. Ajoutez-les sous un nouvel onglet : **Tous**.

Cela garantit que votre vue « Tous les sermons » dispose de ses propres options personnalisables.

---

<a id="example-adding-config-fields"></a>
## Exemple : ajout de champs de configuration

Exemple de champ dupliqué :

```
Label: Show Sermon Description
Name: all_description
Type: Radio (Yes/No)
Default: Yes
```

Ajoutez-en d'autres pour :

* `all_table_grid_list`
* `all_hits`
* `all_icon`
* `all_colour`

Après enregistrement, JCB les inclura dans le `/config.xml` de votre composant.

---

<a id="step-9-compile-and-install-the-component"></a>
## Étape 9 : Compiler et installer le composant

[00:25:38](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h25m38s)

1. Cliquez sur **Compiler le composant**.
2. Installez le fichier ZIP généré via le gestionnaire d'extensions de Joomla.
3. Vérifiez que la nouvelle vue du site **Tous les sermons** apparaît dans les options de vos éléments de menu.
4. Définissez les **autorisations** appropriées sous *Options → Autorisations* (par exemple, autoriser l'accès public).

---

<a id="step-10-test-the-frontend-display"></a>
## Étape 10 : Testez l'affichage du frontend

[00:29:38](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h29m38s)

Après avoir créé et publié des sermons, actualisez l'interface.

Vous devriez maintenant voir :

* Tous les sermons répertoriés dans un tableau paginé.
* Corriger les séries, les catégories et les données d'accès.
* Pagination de travail (jusqu'à 100 éléments par page).
* Mises en page configurables (grille/table/liste) via les options backend.

---

<a id="step-11-verify-config-options"></a>
## Étape 11 : Vérifier les options de configuration

[00:37:10](https://www.youtube.com/watch?v=tiTIG0RZLDQ&t=00h37m10s)

Ouvrez le backend de votre composant → **Options**.
Vous verrez désormais un nouvel onglet **Tous** avec des paramètres tels que :

* Style d'affichage (Tableau/Grille/Liste)
* Afficher les succès
* Afficher la description

Ajustez-les et testez-les pour confirmer que la vue est mise à jour de manière dynamique.

---

<a id="summary"></a>
## Résumé

Vous avez réussi :

* Création d'une requête **Dynamic GET** pour charger tous les éléments.
* Création d'une **nouvelle vue du site** appelée *Tous les sermons*.
* Mise à jour des **modèles et paramètres** pour la nouvelle vue.
* Ajout de **champs de configuration des composants** pour un contrôle de mise en page personnalisé.
* Compilé et testé votre composant dans Joomla.

Ce même processus peut être utilisé pour créer des vues similaires « Tous les éléments » pour n'importe quelle entité dans vos composants construits par JCB.

---

<a id="developer-notes"></a>
## Notes du développeur

* Les GET dynamiques sont stockés sous `/admin/models/get/` après la compilation.
* Des remplacements de modèles peuvent être ajoutés sous `/site/views/[view]/tmpl/`.
* Les champs de configuration correspondent aux définitions XML dans `/admin/config.xml`.
* Utilisez `JRoute::_()` pour les liens compatibles SEF.
* Les paramètres de pagination par défaut sont gérés via le noyau `pagination.php` de Joomla.

---
