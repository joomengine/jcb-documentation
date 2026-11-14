> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="dynamicget"></a>
# DynamicGet

*(Utilisation de Sermon Distributor - Exemple de prédicateur)*

[00:00:00](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
*Cliquez sur les liens d'horodatage pour afficher la section correspondante dans la vidéo.*

---

<a id="overview"></a>
## Aperçu

Dans ce didacticiel, nous explorons comment créer et configurer un **Dynamic Get** dans **Joomla Component Builder (JCB)**. Les requêtes dynamiques sont des requêtes de base de données conçues graphiquement qui définissent la manière dont les données doivent être récupérées, jointes, filtrées et structurées via une interface de création de requêtes de sélection simple. Ils forment une couche d'abstraction visuelle sur les jointures et les filtres SQL, similaire à un générateur de requêtes visuel, un graphe de relations ORM ou un moteur de composition de requêtes personnalisé.

<a id="what-are-dynamic-gets"></a>
### Que sont les Gets Dynamiques ?

Les Gets dynamiques vous permettent de :

- Choisissez une **table principale**
- Rejoignez **plusieurs tables associées**
- Sélectionnez les champs parmi ces jointures
- Appliquez des **filtres**, des **clauses WHERE**, des **commandes** et des **groupements** — le tout dans l'interface graphique.

JCB génère ensuite automatiquement la logique **SQL JOIN** complète, toute **interaction API compatible Joomla** et le **code de modèle PHP** requis pour prendre en charge la requête. Au fur et à mesure que vous progressez dans les étapes ci-dessous, gardez ce modèle conceptuel à l'esprit : chaque champ que vous sélectionnez et chaque jointure que vous créez alimente une requête maintenable et conforme aux normes sans SQL écrit à la main.

En utilisant le composant *Sermon Distributor* comme exemple, ce guide montre comment créer une méthode get `preacher`, configurer les jointures, les filtres et la pagination, et voir comment cela se traduit en code PHP lors de la compilation.

<a id="how-do-dynamic-gets-integrate-into-views"></a>
### Comment les Gets dynamiques s'intègrent-ils dans les vues ?

Chaque **Vue de site** ou **Vue d'administration personnalisée** nécessite un **Objet dynamique principal** qui définit la manière dont les données de son élément ou de sa liste sont extraites de la base de données. Vous pouvez également attacher plusieurs Dynamic Gets supplémentaires à une seule vue, ce qui vous permet de fusionner les données de différentes tables de manière dynamique, propre et cohérente. JCB intègre cette logique directement dans les modèles de votre composant afin que le composant résultant utilise des appels d'API Joomla sécurisés, évite le code répétitif et centralise les définitions de vos ensembles de données.

Cette architecture signifie que les étapes décrites plus loin dans ce document (attribution des get principaux et personnalisés, prévisualisation des valeurs dynamiques et câblage des résultats dans des modèles) ne sont pas des astuces ad hoc. Ils constituent le point culminant d'un flux de travail structuré dans lequel chaque vue extrait des données via ses Dynamic Gets déclarés.

<a id="reset-fork-or-customise"></a>
### Réinitialiser, bifurquer ou personnaliser

Tout comme les autres entités JCB, Dynamic Gets prend en charge un workflow de mise à jour basé sur Git. Vous pouvez initialiser (`Init`) à partir d'un référentiel distant, rester synchronisé via `Reset`, partager des améliorations avec `Push` ou conserver une variante personnalisée à l'aide de `Fork`. Traitez les requêtes dynamiques comme faisant partie des ressources contrôlées en version de votre composant afin que la logique de requête complexe puisse évoluer sans dérive copier-coller.

---

<a id="step-1-selecting-the-data-source"></a>
## Étape 1 : Sélection de la source de données

[00:00:25](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m25s)

1. Accédez à **Dynamic Get Builder** dans JCB.
2. Commencez par un Dynamic Get nouveau ou existant.
3. Sélectionnez votre type de **Source**. Habituellement, vous commencerez par **"Vue back-end"**, car elle offre l'intégration la plus directe avec les données de votre composant.

> **Astuce :** La sélection de « Vue back-end » garantit la stabilité, car l'option « Base de données Joomla » n'est peut-être pas encore entièrement fiable pour tous les composants.

---

<a id="step-2-understanding-the-source-options"></a>
## Étape 2 : Comprendre les options de source

[00:00:50](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m50s)

Il existe trois principales options de source de données :

1. **Vue back-end** - Recommandé. Extrait les données directement de l'une des vues de votre composant.
2. **Base de données Joomla** - Permet de récupérer des données à partir des tables de base de données de *n'importe quel* composant.

* À utiliser avec prudence : des structures ou des relations de tables complexes peuvent causer des problèmes.
3. **Custom Get** - Vous permet d'ajouter manuellement votre propre logique PHP ou de laisser JCB la générer pour vous.

[00:02:55](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m55s)

Lorsque vous utilisez **Custom Get**, vous pouvez :

* Écrivez vous-même le code PHP, ou
* Utilisez "Personnalisé - liste déroulante" pour que JCB génère automatiquement la structure pour vous.

---

<a id="step-3-loading-the-view-fields"></a>
## Étape 3 : Chargement des champs de vue

[00:03:20](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m20s)

1. Après avoir sélectionné la **Vue back-end** (par exemple, *Preacher*),
   JCB charge automatiquement tous les noms de champs de cette vue.
2. Chaque ligne représente un champ qui sera récupéré lors de l'exécution du Get.
3. La colonne de nom de variable définit la façon dont les données apparaîtront dans le modèle.

> **Remarque :** Évitez de modifier les champs système tels que `asset_id`. Vous pouvez supprimer les lignes inutiles, mais laisser les identifiants de clé intacts.

---

<a id="step-4-get-types-and-their-purpose"></a>
## Étape 4 : Obtenez les types et leur objectif

[00:04:23](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m23s)

JCB propose quatre **Get Types** :

| Obtenir le type | Descriptif | Utilisation typique |
| ---------- | --------------------------------- | ------------------- |
| `getitem` | Récupère un seul enregistrement | Vue détaillée |
| `getlistquery` | Récupère plusieurs enregistrements | Vue liste ou tableau |
| `getcustom` | Requête secondaire personnalisée (unique) | Données supplémentaires |
| `getcustoms` | Requête secondaire personnalisée (multiple) | Ensembles de données supplémentaires |

Un seul **un** `getitem` ou `getlistquery` peut exister par vue.
Vous pouvez toutefois ajouter plusieurs méthodes `getcustom` ou `getcustoms`.

> **Conseil :**
> Considérez `getitem` / `getlistquery` comme vos **méthodes principales**, tandis que celles de `getcustom` sont **secondaires**, utilisées pour récupérer les données de support.

---

<a id="step-5-pagination-in-list-queries"></a>
## Étape 5 : Pagination dans les requêtes de liste

[00:06:29](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m29s)

Lorsque vous utilisez `getlistquery`, vous pouvez activer ou désactiver la pagination.

* **Oui** → Limite les résultats en fonction de la **Limite de liste globale** de Joomla (définie sous *Système → Configuration globale → Limite de liste par défaut*).
* **Non** → Renvoie tous les résultats (utile pour les appels AJAX).

Si la pagination est activée, JCB génère automatiquement un code de pagination pour le **modèle** et la **vue**, produisant une navigation de page standard telle que `1, 2, 3`.

> **Remarque :**
> Si Bootstrap ou UIkit n'est pas actif sur votre modèle, le style de pagination devra peut-être être ajusté.

---

<a id="step-6-joining-other-tables-or-views"></a>
## Étape 6 : Rejoindre d'autres tables ou vues

<a id="61---join-data-views"></a>
### 6.1 - Rejoindre des vues de données

[00:08:47](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m47s)

Vous pouvez rejoindre votre source de données principale avec :

* **Catégories (cb_categories)**
* **Autres vues des composants**

Par exemple, l'ajout d'un *champ de catégorie* intègre automatiquement le système de catégories de Joomla dans votre composant.

<a id="62---joint-view-tables"></a>
### 6.2 - Tableaux de vues conjointes

[00:10:23](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m23s)

Tu peux:

* Rejoignez une ou plusieurs lignes à partir d'autres vues
* Renommez les préfixes de champ (par exemple, `series_name`) pour éviter les conflits
* Utilisez les alias **AS** (limités de `a` à `zz`) pour mapper les tables jointes de manière unique

Le *Type de ligne de retour* peut être :

* **Célibataire** → Un enregistrement rejoint
* **Multiple** → Plusieurs enregistrements associés joints

Définissez la relation à l'aide du mappage **Sur champ** (par exemple, `a.series = c.id`).

---

<a id="step-7-reviewing-the-generated-code"></a>
## Étape 7 : Révision du code généré

[00:14:52](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m52s)

Après avoir compilé le composant :

* La méthode du modèle généré inclura votre logique Get.
* Vous pouvez le trouver dans le **modèle frontal** (puisque les Gets y sont généralement utilisés).

Observez comment JCB écrit :

* La requête principale
* Jointures (`series`, `preacher`, `statistics`)
* Alias et objets de retour

Il utilise l'**API de base de données** de Joomla pour citer et joindre des valeurs en toute sécurité, créant ainsi un tableau de champs sélectionnés et leurs alias.

---

<a id="step-8-custom-script-area"></a>
## Étape 8 : Zone de script personnalisée

[00:21:48](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m48s)

Dans **Dynamic Get**, JCB propose une zone *Custom Script* dans laquelle vous pouvez insérer du code PHP qui exécute :

* **Avant de recevoir des objets**, ou
* **Après avoir obtenu les objets**

Cela vous permet de manipuler ou de valider les données une fois la requête Get exécutée.

> **Exemple de cas d'utilisation :**
> Modifiez ou étendez l'ensemble de données après avoir récupéré les éléments, ou filtrez les résultats de manière dynamique avant la récupération.

---

<a id="step-9-filters-where-clauses-and-global-settings"></a>
## Étape 9 : Filtres, clauses Where et paramètres globaux

[00:24:04](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m04s)

Les configurations **Filtre** et **Où** définissent la manière dont vos données sont restreintes.

<a id="filter-types"></a>
### Types de filtres

Les filtres pris en charge incluent :

* Catégories
* Utilisateur, groupe ou niveau d'accès
* Variable ou tableau
* Valeur et valeur répétable

Certains (comme *Date*) ne sont pas encore entièrement implémentés.

<a id="global-variables"></a>
### Variables globales

Définissez les variables **Global** ou **State** pour réutiliser les valeurs Get dans d'autres zones du modèle.
Les valeurs globales sont plus efficaces avec `getitem`, puisque le retour est un enregistrement unique.

> **Exemple :**
> Utilisez `JRequest::getInt('id')` comme filtre pour charger des données en fonction du paramètre URL.

---

<a id="step-10-default-access-and-authorization"></a>
## Étape 10 : Accès et autorisation par défaut

[00:27:38](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m38s)

JCB injecte automatiquement une logique de contrôle d'accès dans chaque modèle Get :

*Identifiant utilisateur
* Groupe
* Niveaux de vue autorisés
* Valeurs d'application et d'entrée

Vous pouvez utiliser ces variables globales dans votre code PHP sans les récupérer manuellement.

---

<a id="step-11-where-and-ordering-logic"></a>
## Étape 11 : Logique « Où » et « Ordre »

[00:29:48](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m48s)

<a id="where"></a>
### Où:

Ajoutez une logique conditionnelle, telle que :

```
a.state = 1
```

Cela garantit que seuls les éléments publiés sont renvoyés.

<a id="ordering"></a>
### Commande :

[00:30:32](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m32s)

Définissez l'ordre des éléments dans la requête :

* Champ : `a.ordering`
* Direction : Ascendant / Descendant

Vous pouvez ajouter plusieurs relevés de commande selon vos besoins.

---

<a id="step-12-dynamic-get-in-use-preacher-example"></a>
## Étape 12 : Utilisation dynamique (exemple de prédicateur)

[00:31:45](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h31m45s)

Dans cet exemple :

* La fonction `getpreacher` (un `getcustom`) récupère un seul prédicateur.
* Il comprend des filtres pour l'état de publication et les niveaux d'accès.
* Il s'intègre à **UIkit**, chargeant dynamiquement les composants CSS/JS requis lors du rendu de la vue.

[00:36:00](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h36m00s)

Component Builder ajoute automatiquement les méthodes d'assistance nécessaires pour identifier et charger ces composants UIkit de manière dynamique en fonction de votre contenu.

---

<a id="step-13-applying-dynamic-get-in-views"></a>
## Étape 13 : Application des vues dynamiques Get in

[00:39:12](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h39m12s)

Une fois configuré, votre **Dynamic Get** peut être attribué à :

* **Vues du site**, ou
* **Vues d'administration personnalisées**

Ils sont chargés de récupérer les données qui alimentent vos vues.
Essentiellement, Dynamic Get définit **quelles** données extraire et **comment** elles sont structurées avant d'être restituées dans votre composant.

---

<a id="summary"></a>
## Résumé

| Fonctionnalité | Descriptif |
| ------------------------------------ | -------------------------------------------- |
| **Types principaux** | `getitem`, `getlistquery` |
| **Extensions personnalisées** | `getcustom`, `getcustoms` |
| **Pagination** | Inclusion automatique en option |
| **Rejoindre des tables** | Prend en charge les jointures simples/multiples avec alias |
| **Filtres/Où** | Créer une logique de requête avancée |
| **Accès mondial** | Injection automatique du contexte Joomla ACL |
| **Script personnalisé** | Ajouter du code PHP pré/post-requête |

---

<a id="key-takeaways"></a>
### Points clés à retenir

* Commencez toujours par **Vue back-end** pour plus de stabilité.
* Utilisez la **pagination** lorsque vous traitez de grands ensembles de données.
* Définissez correctement les **jointures** et les **alias** pour éviter les conflits.
* Tirez parti des **scripts personnalisés** pour une manipulation avancée des données.
* JCB automatise une grande partie du code du modèle : concentrez-vous sur la configuration de la logique plutôt que sur son écriture manuelle.

---
