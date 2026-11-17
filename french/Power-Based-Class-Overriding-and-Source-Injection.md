> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="power-based-class-overriding--source-injection-in-jcb"></a>
# Remplacement de classe basé sur la puissance et injection de source dans JCB

<a id="overview"></a>
## Aperçu

Joomla Component Builder (JCB) permet désormais à **Powers** de placer des classes PHP directement dans les arborescences d'extension `src/` générées pour :

- Composants
-Modules
-Plugins

Ce comportement est déterministe et basé sur l'espace de noms. JCB décide à la fois du chemin cible et si la classe doit **remplacer** une classe générée existante ou **injecter** un nouveau fichier basé sur l'espace de noms Power que vous définissez.

---

<a id="core-rule-namespace-maps-to-destination"></a>
## Règle de base : l'espace de noms est mappé à la destination

JCB résout l'espace de noms Power et l'utilise pour déterminer :

1. **Type d'extension + zone** (Composant/Module/Plugin et Administrateur/Site)
2. **Chemin et nom de classe** en utilisant la notation par points

Si l'espace de noms résolu + le nom de classe correspondent à une classe générée, le pouvoir remplace ce fichier. S'il ne correspond pas à une classe générée existante, JCB ajoute un nouveau fichier.

---

<a id="dynamic-placeholders-for-reusable-powers"></a>
## Espaces réservés dynamiques pour les pouvoirs réutilisables

Pour rendre les pouvoirs réutilisables dans tous les projets, JCB prend en charge les espaces réservés dans les espaces de noms.

<a id="available-placeholders"></a>
### Espaces réservés disponibles

- `[[[NamespacePrefix]]]` -> le préfixe d'espace de noms du projet
- `[[[ComponentNamespace]]]` -> l'espace de noms des composants du projet
- `[[[Componment]]]` -> le nom du composant du projet

> Conservez l'orthographe de l'espace réservé exactement comme indiqué ci-dessus lorsque vous utilisez cette fonctionnalité.

---

<a id="component-examples"></a>
## Exemples de composants

<a id="override-an-existing-generated-component-class"></a>
### Remplacer une classe de composant générée existante

Classe générée cible :

```text
src/Extension/ComponentbuilderComponent.php
```

Espace de noms de puissance :

```text
[[[NamespacePrefix]]]\Component\[[[ComponentNamespace]]]\Administrator\Extension.[[[Componment]]]Component
```

Résultat:

- Les espaces réservés sont résolus.
- L'espace de noms correspond à la classe générée.
- `ComponentbuilderComponent.php` est remplacé par votre classe Power.

<a id="inject-a-new-class-into-administrator-src"></a>
### Injecter une nouvelle classe dans l'administrateur `src/`

Espace de noms de puissance :

```text
[[[NamespacePrefix]]]\Component\[[[ComponentNamespace]]]\Administrator\MyFolder.MyOwnClass
```

Chemin résultant :

```text
src/MyFolder/MyOwnClass.php
```

<a id="inject-a-new-class-into-site-src"></a>
### Injecter une nouvelle classe dans le site `src/`

Espace de noms de puissance :

```text
[[[NamespacePrefix]]]\Component\[[[ComponentNamespace]]]\Site\MyFolder.MyOwnClass
```

Chemin résultant :

```text
site/src/MyFolder/MyOwnClass.php
```

---

<a id="module-examples"></a>
## Exemples de modules

<a id="override-module-dispatcher"></a>
### Remplacer le répartiteur de module

Classe générée cible :

```text
src/Dispatcher/Dispatcher.php
```

Espace de noms de puissance :

```text
[[[NamespacePrefix]]]\Module\CPanelRedirect\Administrator\Dispatcher.Dispatcher
```

Résultat:

- Le répartiteur de module généré est remplacé.
- La classe de puissance devient le répartiteur actif.

<a id="inject-a-new-class-into-module-administrator-src"></a>
### Injecter une nouvelle classe dans l'administrateur du module `src/`

```text
[[[NamespacePrefix]]]\Module\CPanelRedirect\Administrator\MyFolder.MyOwnClass
```

-> `src/MyFolder/MyOwnClass.php`

<a id="inject-a-new-class-into-module-site-src"></a>
### Injecter une nouvelle classe dans le site de modules `src/`

```text
[[[NamespacePrefix]]]\Module\CPanelRedirect\Site\MyFolder.MyOwnClass
```

-> `site/src/MyFolder/MyOwnClass.php`

---

<a id="plugin-examples"></a>
## Exemples de plugins

<a id="override-an-existing-plugin-class"></a>
### Remplacer une classe de plugin existante

Classe générée cible :

```text
src/Extension/ComponentbuilderPowersAutoloaderCompiler.php
```

Espace de noms de puissance :

```text
[[[NamespacePrefix]]]\Plugin\Extension\ComponentbuilderPowersAutoloaderCompiler\Extension.ComponentbuilderPowersAutoloaderCompiler
```

Résultat:

- La classe d'extension de plugin générée est remplacée.
- La classe Power devient la classe compilée.

<a id="inject-a-new-class-into-plugin-src"></a>
### Injecter une nouvelle classe dans le plugin `src/`

```text
[[[NamespacePrefix]]]\Plugin\Extension\ComponentbuilderPowersAutoloaderCompiler\MyFolder.MyOwnClass
```

-> `src/MyFolder/MyOwnClass.php`

---

<a id="dot-notation-mapping"></a>
## Mappage de notation par points

À l'intérieur du segment final de l'espace de noms, la notation par points contrôle les dossiers et les noms de classe.

Exemple:

```text
MyFolder.SubFolder.MyClass
```

Cartes vers :

```text
MyFolder/SubFolder/MyClass.php
```

Règle:

- Tout ce qui se trouve avant le dernier point devient un dossier.
- Tout ce qui se trouve après le dernier point devient le nom de la classe.

---

<a id="using-injectedoverridden-classes-in-your-project"></a>
## Utilisation de classes injectées/remplacées dans votre projet

Une fois que JCB place la classe Power au bon emplacement `src/`, vous pouvez l'utiliser comme classe d'extension normale et la référencer via vos flux de travail JPK/code personnalisé existants.

---

<a id="important-trade-off"></a>
## Compromis important

Il s'agit d'une fonctionnalité de contrôle avancée délibérée :

- Si vous remplacez une classe générée, vous êtes propriétaire de cette implémentation de classe.
- JCB ne régénérera pas cette classe à moins que le remplacement de puissance ne soit supprimé.

Utilisez-le lorsque vous avez besoin d'un contrôle architectural explicite et d'une personnalisation à long terme au niveau de la source.

---

<a id="why-this-matters-for-superpower-areas"></a>
## Pourquoi c'est important pour les zones de superpuissance

Cette capacité transforme l’utilisation de JCB Superpower en un système d’injection à la source fiable :

- placement de classe déterministe
- comportement de remplacement explicite
- modèles d'espace de noms portables utilisant des espaces réservés
- logique avancée réutilisable sur plusieurs projets

---

<a id="source-discussion"></a>
## Discussion sur les sources

Ce document a été créé à partir de la discussion sur les fonctionnalités :

- <https://github.com/orgs/joomengine/discussions/1012>
