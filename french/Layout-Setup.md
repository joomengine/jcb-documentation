> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="layout-setup"></a>
# Configuration de la mise en page

> **Tutoriel vidéo :** [Regarder sur YouTube](https://www.youtube.com/watch?v=52OLSZio0F8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
> (*Cliquez sur les liens d'horodatage ci-dessous pour accéder à des sections spécifiques du didacticiel.*)

---

<a id="introduction-to-layouts"></a>
## Introduction aux mises en page

[00:00:00](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m00s)

Dans **Joomla Component Builder (JCB)**, les mises en page sont utilisées pour **réutiliser le code d'affichage** dans plusieurs modèles ou vues de site. Cela permet de maintenir la cohérence et de réduire la duplication. Le [JCB Layouts overview](./JCB-Layouts.md) explique comment initialiser, réinitialiser, pousser et forker les référentiels de mise en page dans JCB afin que les techniques de cette procédure pas à pas restent contrôlées en version d'un projet à l'autre.

Les mises en page vous permettent :

* Partagez la logique d'affichage entre les vues du site.
* S'adapter dynamiquement au contexte (vue, données et paramètres globaux).
* Simplifiez la gestion des modèles en séparant la logique de l'affichage.

Avant de créer ou d'utiliser des mises en page, comprenez **quelle vue du site appelle la mise en page**, car les paramètres globaux peuvent varier selon la vue.

---

<a id="how-layouts-work-with-dynamic-gets"></a>
## Comment fonctionnent les mises en page avec les GET dynamiques

[00:00:34](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m34s)

Chaque **Dynamic GET** cible une **vue de site** spécifique.
Par exemple, l'requête dynamique `sermon (preacher.id)` est conçue pour la vue **Preacher**.

Dans le script personnalisé, vous pouvez définir une **clé d'affichage** - dans ce cas, `"Preacher"`.
Cela garantit :

* Seul l'élément pertinent est transmis à la mise en page (pas la liste complète).
* La mise en page adapte son affichage en fonction de la vue appelante.

```php
// Example snippet from a layout context
$viewKey = 'preacher';
$item = $displayData; // the specific item passed from Dynamic Get
```

Vous pouvez ensuite personnaliser la sortie de la mise en page en fonction du `$viewKey`.

---

<a id="how-templates-call-layouts"></a>
## Comment les modèles appellent les mises en page

[00:01:39](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h01m39s)

Les modèles peuvent appeler des mises en page à l'aide de `JLayoutHelper::render()`.

Exemple - à partir du modèle **liste de sermons** :

[00:01:54](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h01m54s)

Le modèle parcourt les éléments, prépare les paramètres et transmet les données à la mise en page.

```php
foreach ($this->items as $item) {
    $item->params = $this->params;
    $item->description = JHtmlString::truncate($item->description, 90);
    echo JLayoutHelper::render('sermonlist.item', $item);
}
```

[00:02:46](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h02m46s)

Cet appel `JLayoutHelper::render()` affichera chaque élément de liste en fonction de la présentation sélectionnée.

---

<a id="sermon-list---item-layout"></a>
## Liste de sermons – Disposition des éléments

[00:03:08](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h03m08s)

Dans la **disposition des éléments de la liste de sermons**, JCB transmet l'objet `$displayData`, qui représente le `$item` actuel.

Exemple:

```php
$item = $displayData;
$title = $item->get('title');
```

Cela permet aux mises en page d'accéder à tous les champs, paramètres et paramètres globaux via `$displayData`.

---

<a id="-using-the-view-key"></a>
## 🗝 Utilisation de la clé d'affichage

[00:03:56](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h03m56s)

Les mises en page peuvent utiliser une **clé de vue** pour déterminer la vue à afficher (par exemple, Preacher, Series ou Category).

En cochant cette clé, vous pouvez créer un comportement dynamique :

* Afficher ou masquer des données spécifiques en fonction de la vue.
* Utilisez différents paramètres globaux basés sur `$viewKey`.

Cela permet une réutilisation flexible de la même mise en page dans plusieurs contextes.

---

<a id="layout-template-integration-via-custom-script"></a>
## Intégration de modèle de mise en page via un script personnalisé

[00:05:11](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h05m11s)

Dans les modèles, JCB utilise des espaces réservés tels que `[[[sview]]]` pour insérer dynamiquement le **nom de la vue du site**.

Exemple:

```php
<div class="[[[sview]]]-list">
    <!-- Dynamic view-specific layout -->
</div>
```

Cela permet de réutiliser un modèle pour plusieurs vues de site sans dupliquer les fichiers.

---

<a id="dynamic-custom-views-using-templates"></a>
## Vues personnalisées dynamiques à l'aide de modèles

[00:05:46](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h05m46s)

L'espace réservé `[[[sview]]]` assure l'insertion dynamique du nom de la vue du site.
Il extrait les valeurs des **paramètres globaux du composant** - par exemple, `sermon_list_style`.

Le modèle s'ajustera ensuite automatiquement en fonction de la vue actuelle (Prédicateur, Série ou Catégorie).

---

<a id="configxml-and-global-parameters"></a>
## config.xml et paramètres globaux

[00:07:17](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h07m17s)

Ces paramètres sont définis dans le fichier **config.xml** de votre composant.

À l’intérieur, vous trouverez des paramètres tels que :

* `preacher_list_style`
* `series_list_style`
* `category_list_style`

Ceux-ci déterminent le comportement d’affichage par vue.

En recherchant `sermon_list_display`, vous verrez comment JCB utilise dynamiquement la même logique pour chaque vue.

---

<a id="layout-concept-explained"></a>
## Concept de mise en page expliqué

[00:09:26](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h09m26s)

Les mises en page fonctionnent comme des modèles mais offrent **plus de flexibilité** :

* Vous pouvez inclure PHP et la logique dynamique.
* Vous pouvez les réutiliser sur plusieurs vues de site.
* Ils peuvent gérer toutes les données transmises via `$displayData`.

**Conseil :** Si vous n'êtes pas familier avec PHP, vous pouvez gérer la logique d'affichage directement dans la vue du site. Les mises en page sont destinées à un développement plus propre et modulaire.

---

<a id="layout-custom-script-area"></a>
## Mise en page Zone de script personnalisée

[00:11:02](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m02s)

Chaque mise en page dans JCB comprend une **zone de script personnalisée** (dans l'en-tête du fichier de mise en page).
Cela vous permet :

* Ajoutez PHP ou JavaScript en ligne.
* Modifier dynamiquement `$displayData`.
* Accédez aux paramètres globaux.

```php
<?php
$global = $displayData;
$paramValue = $global->get('my_field');
?>
```

---

<a id="using-a-layout-inside-another-layout"></a>
## Utiliser une mise en page dans une autre mise en page

[00:11:32](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m32s)

Les mises en page peuvent **inclure d'autres mises en page** en utilisant :

```php
echo JLayoutHelper::render('sub.layout.name', $subData);
```

**Important:**

* `$this` n'est pas disponible dans les mises en page.
* Comptez toujours sur `$displayData` pour transmettre des données entre eux.

---

<a id="summary"></a>
## Résumé

| Concepts | Objectif | Référence clé |
| ------------------ | -------------------- | ------------------------------------------------------------------- |
| **Mise en page** | Code d'affichage réutilisable | [00:00:00](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m00s) |
| ** OBTENIR dynamique ** | Transmettre les données aux mises en page | [00:00:34](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h00m34s) |
| **Modèles** | Appeler les mises en page dynamiquement | [00:01:39](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h01m39s) |
| **Voir la clé** | Identifier la vue du site | [00:03:56](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h03m56s) |
| **config.xml** | Définir les options globales | [00:07:17](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h07m17s) |
| **Scripts personnalisés** | Ajouter une logique dynamique | [00:11:02](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m02s) |
| **Mise en page imbriquée** | Mises en page à l'intérieur des mises en page | [00:11:32](https://www.youtube.com/watch?v=52OLSZio0F8&t=00h11m32s) |

---

<a id="pro-tips"></a>
## Conseils de pro

* Utilisez des **clés de vue significatives** pour gérer la logique par vue de site.
* Gardez tous les **fichiers de mise en page modulaires** - un par concept d'affichage.
* Référencez les **paramètres globaux** dans `config.xml` pour standardiser l'apparence.
* En cas de doute, vérifiez `$displayData` pour voir quelles données sont disponibles.
* Réutilisez les mises en page pour conserver les principes **DRY** (Don't Repeat Yourself).

---
