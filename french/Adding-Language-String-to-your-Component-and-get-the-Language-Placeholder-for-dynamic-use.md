> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-language-strings-and-dynamic-placeholders-in-jcb"></a>
# Ajout de chaînes de langue et d'espaces réservés dynamiques dans JCB

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Ce guide explique comment **ajouter une chaîne de langue** à votre composant dans Joomla Component Builder (JCB) et comment générer un **espace réservé de langue** pour une **utilisation dynamique** - particulièrement utile lorsque vous travaillez dans des classes ou des tableaux où l'appel direct `JText` ne peut pas être utilisé.

---

<a id="understanding-language-strings-in-jcb"></a>
## Comprendre les chaînes de langage dans JCB

Lors du développement de composants Joomla, vous utilisez souvent la fonction `JText` pour traduire des chaînes de manière dynamique. Normalement, lorsque JCB compile votre composant :

* La chaîne à l'intérieur de `JText` est ajoutée à votre fichier de langue.
* L'espace réservé remplace la chaîne dans le code compilé.
* Le système Joomla traduit cet espace réservé chaque fois qu'il est affiché.

Exemple:

```php
echo JText::_('COM_MYCOMPONENT_HELLO_WORLD');
```

Lors de la compilation, JCB s'assure automatiquement que `COM_MYCOMPONENT_HELLO_WORLD` est écrit dans le fichier de langue du composant avec son texte de traduction.

---

<a id="when-you-need-only-the-placeholder"></a>
## Lorsque vous n'avez besoin que de l'espace réservé

[00:00:59](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m59s)

Parfois, vous aurez peut-être besoin de **uniquement l'espace réservé à la langue**, et non de la traduction complète au moment de la compilation - par exemple, lorsque vous travaillez dans un **tableau de classes**.

Exemple de scénario :
Vous disposez d'une classe avec un tableau de propriétés de champ (comme `listclass`, `escape`, `display` ou `validate`) et vous souhaitez référencer la chaîne traduite ultérieurement au moment de l'exécution, pas immédiatement lorsque JCB la compile.

Dans de tels cas, vous ne pouvez pas utiliser directement `JText` dans le tableau, car cela tenterait de traduire immédiatement. Vous n'avez besoin que de la **chaîne d'espace réservé** dans le code compilé, prête pour une traduction ultérieure.

---

<a id="using-the-justtext-feature"></a>
## Utilisation de la fonctionnalité `JustTEXT`

[00:01:32](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m32s)

Pour gérer ce cas d'utilisation, JCB introduit un mot-clé spécial :

<a id="justtext"></a>
### `JustTEXT`

Cette fonctionnalité :

* Ajoute la chaîne à votre fichier de langue (comme le fait normalement JCB).
* Insère **uniquement l'espace réservé** (pas la traduction) dans votre script PHP.
* Vous permet de le traduire **plus tard dans le code** lorsque vous décidez d'appeler `JText` dessus.

Ceci est particulièrement utile pour les flux de travail de traduction dynamiques ou lors d'une boucle dans des tableaux où la traduction a lieu une fois que certaines conditions sont remplies.

---

<a id="how-jcb-compiles-it"></a>
## Comment JCB le compile

[00:02:16](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m16s)

`JustTEXT` ressemble à un appel de classe ou de fonction, mais ce n'est pas réellement une classe ou une fonction PHP.
Il s'agit d'un **marqueur** reconnu par le compilateur JCB, qui le traite lors de la compilation et le remplace de manière appropriée.

Par exemple:

```php
JustTEXT::_('COM_MYCOMPONENT_VALIDATION_ERROR');
```

Après compilation, JCB génère :

```php
'COM_MYCOMPONENT_VALIDATION_ERROR'
```

Cela signifie que la chaîne d'espace réservé est insérée, pas encore traduite. Vous pourrez ensuite l'utiliser comme :

```php
JText::_($value);
```

- où `$value` était l'espace réservé créé par `JustTEXT`.

---

<a id="applying-it-in-your-class-arrays"></a>
## L'appliquer dans vos tableaux de classes

[00:02:49](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m49s)

Considérez cet exemple courant au sein d'une classe qui définit les propriétés d'un champ :

```php
$extra_field_properties = array(
    'listclass' => JustTEXT::_('COM_MYCOMPONENT_FIELD_LISTCLASS_DESC'),
    'escape'    => JustTEXT::_('COM_MYCOMPONENT_FIELD_ESCAPE_DESC'),
    'display'   => JustTEXT::_('COM_MYCOMPONENT_FIELD_DISPLAY_DESC'),
    'validate'  => JustTEXT::_('COM_MYCOMPONENT_FIELD_VALIDATE_DESC')
);
```

Après compilation, cela devient :

```php
$extra_field_properties = array(
    'listclass' => 'COM_MYCOMPONENT_FIELD_LISTCLASS_DESC',
    'escape'    => 'COM_MYCOMPONENT_FIELD_ESCAPE_DESC',
    'display'   => 'COM_MYCOMPONENT_FIELD_DISPLAY_DESC',
    'validate'  => 'COM_MYCOMPONENT_FIELD_VALIDATE_DESC'
);
```

Plus tard dans votre logique, lorsque vous parcourez ce tableau, vous pouvez traduire les valeurs de manière dynamique :

```php
foreach ($extra_field_properties as $key => $description) {
    echo JText::_($description);
}
```

Cela vous offre une gestion de traduction propre et flexible tout en gardant les espaces réservés intacts jusqu'à ce que vous en ayez besoin.

---

<a id="compilation-result-example"></a>
## Exemple de résultat de compilation

[00:03:11](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m11s)

Lorsque JCB compile, vous remarquerez :

* Les entrées `JustTEXT` sont converties en espaces réservés de chaîne simple.
* Les chaînes sont toujours incluses dans le fichier `.ini` de votre langue.
* Vous pouvez utiliser ces espaces réservés ultérieurement n'importe où dans votre composant.

Exemple d'extrait avant et après compilation :

**Avant la compilation :**

```php
'display' => JustTEXT::_('COM_MYCOMPONENT_FIELD_DISPLAY_DESC'),
```

**Après la compilation :**

```php
'display' => 'COM_MYCOMPONENT_FIELD_DISPLAY_DESC',
```

Ces espaces réservés restent disponibles pour une utilisation ultérieure avec `JText::_()`.

---

<a id="summary"></a>
## Résumé

[00:04:09](https://www.youtube.com/watch?v=_mXlbAO79J8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m09s)

Pour résumer :

* Utilisez normalement `JText::_()` lorsque vous souhaitez une **traduction immédiate**.
* Utilisez `JustTEXT::_()` lorsque vous souhaitez **uniquement l'espace réservé** ajouté et la **traduction différée**.
* Les deux méthodes garantissent que vos chaînes sont écrites en toute sécurité dans le fichier de langue.
* `JustTEXT` vous donne plus de contrôle lors de la gestion des **tableaux**, du **contenu dynamique** ou de la **logique basée sur les classes** qui traite les chaînes ultérieurement.

---

<a id="pro-tip"></a>
### Conseil de pro

Si vous disposez d'une logique dans laquelle les chaînes de langage sont utilisées de manière conditionnelle (par exemple, à l'intérieur de boucles, de tableaux ou de fonctions personnalisées), `JustTEXT` maintient votre code flexible et vos traductions organisées - sans forcer une interprétation précoce lors de la compilation.

---
