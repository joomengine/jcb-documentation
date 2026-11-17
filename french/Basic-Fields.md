> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="joomla-component-builder---basic-fields"></a>
# Joomla Component Builder - Champs de base

<a id="tutorial-reference"></a>
### Référence du didacticiel

[Vidéo : Champs de base](https://www.youtube.com/watch?v=9NO2rKnC6Ug&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
---

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=0s)

Dans ce didacticiel, nous explorons comment créer des **champs** dans Joomla Component Builder (JCB).
Les champs sont fondamentaux pour tout composant car ils définissent la **structure de données**, les **entrées de formulaire** et les **mappages de base de données** de votre composant personnalisé. Si vous avez besoin d'un rappel sur la mesure dans laquelle un seul champ contrôle (schéma de base de données, rendu, validation, ACL et partage), commencez par la [Présentation des champs JCB](./JCB-Fields.md), puis revenez ici pour une présentation pratique.

Il existe deux catégories de champs dans JCB :

1. **Types de champs courants (de base)** - Ce sont des champs Joomla standard tels que texte, liste, radio, éditeur, couleur, catégorie, etc.
2. **Types de champs avancés (personnalisés)** - Il s'agit de champs spécialisés ou dynamiques qui interagissent avec d'autres données de composants. Ceux-ci sont abordés dans des didacticiels ultérieurs après l'introduction des vues d'administration et de site.

> **Conseil :** Avant de créer des champs personnalisés, il est important de comprendre comment les champs et les vues sont connectés dans JCB.

---

<a id="creating-a-new-field-type-text-field-example"></a>
## Création d'un nouveau type de champ (exemple de champ de texte)

[00:01:04](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=64s)

Pour créer un nouveau champ :

1. Accédez à **Administrateur Joomla → Composants → Générateur de composants → Champs**.
2. Cliquez sur **Nouveau champ**.
3. Choisissez **Texte** comme type de champ.

Une fois sélectionné, JCB chargera automatiquement les paramètres de champ par défaut définis par le type de champ sélectionné.

<a id="understanding-mysql-data-types"></a>
### Comprendre les types de données MySQL

[00:01:29](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=89s)

Chaque champ correspond à un type de colonne MySQL, tel que :

* `VARCHAR`
* `TEXT`
* `MEDIUMTEXT`
* `LONGTEXT`

Vous pouvez modifier ces types de données dans JCB.
Cette flexibilité permet aux développeurs de concevoir des structures de bases de données plus **complexes et évolutives**.

> **Remarque :** Cette fonctionnalité est destinée aux développeurs ayant une expérience SQL. JCB permet une personnalisation avancée plutôt que de vous limiter à des contraintes « sans code ».

---

<a id="database-index-and-null-options"></a>
## Index de base de données et options nulles

[00:03:15](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=195s)

Chaque champ peut avoir :

* **Longueur :** Limite de caractères pour le champ.
* **Valeur par défaut :** Valeur prédéfinie si aucune donnée n'est saisie.
* **Type d'index :** `KEY` ou `UNIQUE KEY`.

> Définir un champ comme **Unique** signifie qu'aucune valeur en double ne peut exister dans cette colonne.
> Joomla gère généralement l'unicité (par exemple dans les alias), cela est donc rarement nécessaire.

Le **Null Switch** détermine si la colonne de la base de données peut être vide.

---

<a id="store-method-default-json-base64-encryption"></a>
## Méthode de stockage (par défaut, JSON, Base64, cryptage)

[00:04:28](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=268s)

La **méthode store** définit la manière dont les données sont stockées dans la base de données :

* **Par défaut :** Méthode standard pour la plupart des champs.
* **JSON :** Utilisé pour stocker des tableaux (par exemple, des sélections multiples dans des champs de liste ou des cases à cocher).
* **Base64 :** Encode les données, souvent utilisées pour stocker du code ou des scripts personnalisés.
* **Chiffrement :** Pour des besoins de sécurité avancés (facultatif, complexe à mettre en œuvre).

> **Exemple :**
>
> * Un champ de case à cocher avec plusieurs valeurs doit utiliser JSON.
> * Les champs de balises sont gérés différemment et ne nécessitent pas d'encodage JSON.

JCB garantit automatiquement que les données des cases à cocher sont stockées sous forme de JSON valide, même si Joomla ne les gère pas correctement de manière native.

---

<a id="inspecting-compiled-fields-in-the-ui"></a>
## Inspection des champs compilés dans l'interface utilisateur

[00:07:42](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=462s)

Lorsque JCB compile votre composant, il inclut des commentaires détaillés dans les fichiers de modèle XML et PHP indiquant **où chaque champ est implémenté**.

Si un champ ne fonctionne pas comme prévu, ouvrez les fichiers compilés pour localiser et inspecter les lignes de code pertinentes. Cela aide les développeurs à déboguer ou à personnaliser le comportement avec précision.

---

<a id="example-email-field-creation"></a>
## Exemple : Création d'un champ d'e-mail

[00:10:28](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=628s)

Créons un **champ e-mail** à titre d'exemple :

| Paramètre | Valeur |
| ------------ | ---------- |
| Type de champ | `Text` |
| Nom | `email` |
| Étiquette | `Enter Email` |
| Type de données | `VARCHAR(255)` |
| Obligatoire | Non |
| Méthode de stockage | Par défaut |
| Validation | `Email` |

> **Conseil de validation :**
> Joomla inclut des types de validation intégrés (comme `email`, `url`, `number`).
> Une validation personnalisée peut être ajoutée en écrivant un validateur PHP et en le mappant via le système de fichiers personnalisés JCB.

---

<a id="targeting-fields-with-css-and-javascript"></a>
## Ciblage des champs avec CSS et JavaScript

[00:14:10](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=850s)

Chaque champ dans JCB possède un **ID HTML** unique suivant cette structure :

```
#jform_FIELDNAME
```

Par exemple, pour cibler le champ `email` :

```css
#jform_email {
  color: red;
}
```

Ou avec jQuery :

```javascript
jQuery('#jform_email').val('example@domain.com');
```

<a id="adding-scripts-or-styles-in-fields"></a>
### Ajout de scripts ou de styles dans les champs

Vous pouvez ajouter du **CSS** ou **JavaScript** personnalisé directement dans la configuration du champ sous la zone **Script**.
Ces scripts suivent le champ partout où il est utilisé dans les vues, permettant un comportement dynamique réutilisable.

---

<a id="repeatable-fields-with-custom-scripts"></a>
## Champs répétables avec des scripts personnalisés

[00:17:49](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1069s)

Le système par défaut de Joomla ne prend pas en charge certains types de champs (comme Date) dans les **Champs répétables**.
Cependant, JCB permet une personnalisation avancée à l'aide de PHP et JS en ligne dans la **zone de script de champ**.

Exemple (simplifié) :

```php
<?php
// Inside the field script
JHtml::_('jquery.framework');
?>
<script>
  jQuery(function() {
    jQuery('#course_date_fields_date').datepicker();
  });
</script>
```

> **Important :**
> Ce script est attaché au champ répétable, et non au champ de texte lui-même, garantissant qu'il s'applique dynamiquement à tous les éléments répétés.

---

<a id="list-field-static-options"></a>
## Champ de liste (options statiques)

[00:20:26](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1226s)

Pour créer un champ **Liste** :

* Type de champ : `List`
* Format des options : `value|label,value2|label2,...`

Exemple:

```
0|Select an option,1|Option One,2|Option Two
```

Si la valeur et l'étiquette sont identiques, vous pouvez omettre le canal (`|`).

> **Listes dynamiques :**
> Des didacticiels ultérieurs montreront comment remplir dynamiquement des listes à partir d'autres tables en utilisant les fonctionnalités de champ avancées de JCB.

---

<a id="radio-button-example"></a>
## Exemple de bouton radio

[00:24:38](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1478s)

Les boutons radio fonctionnent de la même manière que les champs de liste, mais sont idéaux pour **deux à quatre options**.

Utilisez la même syntaxe :

```
1|Yes,0|No
```

Évitez les guillemets à l’intérieur des valeurs. Utilisez plutôt des entités HTML (par exemple, `&quot;`).

---

<a id="color-field-example"></a>
## Exemple de champ de couleur

[00:26:54](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1614s)

Le champ de couleur permet de choisir une couleur avec une valeur par défaut.

* Tapez : `Color`
* Libellé : par exemple, « Sélectionner la couleur »
* Nom : identifiant en minuscule (par exemple, `text_color`)

Si vous modifiez le type manuellement, JCB l'ignore car le champ de couleur est **verrouillé** sur ses paramètres prédéfinis.

---

<a id="showon-attribute-example"></a>
## Exemple d'attribut Showon

[00:27:46](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1666s)

L'attribut **Showon** permet une visibilité conditionnelle des champs.
Par exemple, pour afficher un champ uniquement lorsqu'un autre champ a une certaine valeur :

```
view:1
```

Ou pour plusieurs valeurs :

```
view:[1,4]
```

> JCB étend également le *showon* par défaut de Joomla avec son propre **système conditionnel avancé**, permettant des dépendances plus complexes entre les champs.

---

<a id="category-field-example"></a>
## Exemple de champ de catégorie

[00:29:18](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1758s)

Pour ajouter la prise en charge native des **Catégories** de Joomla :

* Type de champ : `Category`
* Extension : le nom de votre composant (par exemple, `com_example`)

Vous pouvez également cibler une vue spécifique :

```
com_example.viewname
```

> Celui-ci intègre automatiquement le système de gestion des catégories de Joomla dans votre composant.

---

<a id="editor-field-example"></a>
## Exemple de champ d'éditeur

[00:32:10](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=1930s)

Le **Champ Éditeur** intègre l'éditeur de contenu Joomla (TinyMCE ou alternative) dans votre formulaire.

Vous pouvez configurer :

* Quel éditeur charger
* Que ce soit pour afficher ou masquer les boutons de l'éditeur
* Options de filtre

Ces paramètres suivent le comportement des formulaires standard de Joomla.

---

<a id="media-field-example"></a>
## Exemple de champ multimédia

[00:33:26](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2006s)

Le **Champ Média** permet la sélection d'images.

* Répertoire par défaut : `/images/`
* Répertoire personnalisé : `/images/yourfolder/`
* Aperçu facultatif : l'aperçu au survol peut être activé
* Prend en charge `showon` et les attributs standard

> Joomla limite actuellement les champs Médias au répertoire `/images/`.

---

<a id="notes-field-example"></a>
## Exemple de champ de notes

[00:34:42](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2082s)

**Notes** sont des éléments non saisis utilisés pour afficher du texte informatif entre les champs.
Vous pouvez positionner les notes avant ou après d'autres champs à l'aide de la section **Informations sur le champ**.

---

<a id="translation-and-language-strings"></a>
## Traduction et chaînes de langue

[00:36:31](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2191s)

Chaque attribut de champ peut être marqué comme **Traductible**.
Lorsqu'il est activé, JCB automatiquement :

1. Convertit l'étiquette ou la valeur en constante de langage.
2. L'ajoute au fichier de langue de votre composant.
3. Remplace l'étiquette/valeur XML par la chaîne de langue.

Exemple:

Étiquette : `Acronym`
→ JCB le convertit en `COM_EXAMPLE_FIELD_ACRONYM_LABEL`.

> **Conseil :** Cela garantit que votre composant prend en charge les traductions multilingues de manière transparente.

---

<a id="summary"></a>
## Résumé

[00:38:59](https://www.youtube.com/watch?v=9NO2rKnC6Ug&t=2339s)

Vous avez maintenant appris à créer et configurer des **champs de base** dans Joomla Component Builder, notamment :

* Champs Texte, E-mail, Liste, Radio, Couleur, Catégorie, Éditeur, Média et Notes.
* Méthodes de stockage des données (par défaut, JSON, Base64).
* Visibilité conditionnelle (Showon).
* Ajout de scripts et de traductions.

---
