> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-custom-codes-overview"></a>
# Aperçu des codes personnalisés JCB

Joomla Component Builder (JCB) vous permet de centraliser une logique sur mesure dans des **Codes personnalisés** afin que vous puissiez réutiliser, partager et maintenir automatiquement le comportement de plusieurs composants. La fonctionnalité couvre désormais deux workflows complémentaires :

1. **Blocs de code réutilisables avec injection d'arguments** – étiquetés **JCB (manuel)** à l'intérieur de l'interface.
2. **Remplacements de fichiers persistants gérés par des balises d'insertion/remplacement** – étiquetés **Hash (automatisation)**.

Cette page résume les deux approches, explique comment elles interagissent avec d'autres outils JCB et propose des liens vers les didacticiels plus approfondis déjà présents dans l'ensemble de documentation.

---

<a id="1-reusable-code-injection-with-customcode"></a>
## 1. Injection de code réutilisable avec `[CUSTOMCODE=...]`

La méthode **JCB (manuel)** vous permet de définir une seule fois un fragment de code, puis de l'injecter partout où JCB restitue le code (PHP, XML, JavaScript, HTML, etc.). Référencez le fragment avec un espace réservé tel que :

```text
[CUSTOMCODE=mainReadmePackageFooter]
```

Pour transmettre des valeurs dynamiques, ajoutez une liste d'arguments séparés `+` :

```text
[CUSTOMCODE=mainReadmePackageFooter+foo,bar,baz]
```

Dans la définition du code personnalisé, vous pouvez référencer ces valeurs via des espaces réservés de base zéro :

* `[[[arg0]]]` → `foo`
* `[[[arg1]]]` → `bar`
* `[[[arg2]]]` → `baz`

> ✅ **Faites correspondre les arguments aux espaces réservés.** Si votre code fait référence à `[[[argN]]]`, vous devez fournir une valeur pour chaque espace réservé lors de l'injection de l'extrait.

<a id="encoding-reserved-characters"></a>
### Encodage des caractères réservés

Les arguments sont analysés par JCB, les caractères réservés doivent donc être codés en HTML avant d'atteindre votre code personnalisé :

| Caractère | Forme codée |
| --- | --- |
| `[` | `&#91;` |
| `]` | `&#93;` |
| `,` | `&#44;` |
| `+` | `&#43;` |
| `=` | `&#61;` |

<a id="scope-and-limitations"></a>
### Portée et limites

* Des codes personnalisés manuels peuvent être injectés dans **n'importe quelle zone de code JCB** et même **à l'intérieur d'autres codes personnalisés**.
* Ils **ne peuvent pas** être utilisés dans leur propre définition ou dans les blocs de code **Hash automation**.
* Les espaces réservés aux arguments sont actuellement à sens unique ; une fois compilé, le projet généré ne contient plus les marqueurs `[[[argX]]]`. Pour mettre à jour un code personnalisé basé sur des arguments, modifiez-le dans **l'interface utilisateur JCB** et recompilez-le.

Pour une présentation vidéo de l'interface, voir [Code personnalisé manuel JCB](./JCB-manual-custom-code-implementation.md) et [Réutiliser le code personnalisé](./Reuse-Custom-Code.md).

---

<a id="2-persistent-file-overrides-with-hash-automation"></a>
## 2. Remplacements de fichiers persistants avec l'automatisation du hachage

Lorsque le composant compilé par JCB réside sur la même instance Joomla, vous pouvez injecter ou remplacer des extraits directement dans les fichiers générés. Enveloppez le bloc cible avec des balises de commentaires spéciales et JCB détectera, stockera et réappliquera le code sur les futures compilations. Exemple de balise d'insertion PHP :

```php
/***[INSERT<>$$$$]***/
// your code
/***[/INSERT<>$$$$]***/
```

Dans les coulisses de JCB :

1. Analyse votre installation pour les paires de balises.
2. Extrait le contenu et l'enregistre dans l'interface utilisateur du code personnalisé.
3. Suit le chemin du fichier et le contexte du numéro de ligne.
4. Réinjecte le code chaque fois que vous compilez à nouveau.

L'automatisation d'insertion/remplacement prend actuellement en charge les contextes **PHP** et **HTML**. Si l'emplacement d'origine devient ambigu, JCB commente le bloc, vous avertit lors de la compilation et conserve le code afin que vous puissiez le reloger manuellement.

Reportez-vous à [Importation automatique du code personnalisé pendant la compilation](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) pour connaître le cycle de vie complet, y compris la manière dont les hachages sont calculés et comment redéclencher les mises à jour.

---

<a id="3-reverse-engineering-language-strings"></a>
## 3. Chaînes de langage d'ingénierie inverse

Lorsque les importations automatisées capturent du code tel que `Text::_('COM_EXAMPLE_LABEL')`, JCB traduit automatiquement la constante en son texte lisible par l'homme avant de l'afficher dans l'éditeur. Cela facilite la maintenance de vos chaînes de langue ainsi que des extraits de code qui les utilisent.

---

<a id="4-version-control-forking-and-collaboration"></a>
## 4. Contrôle de version, forking et collaboration

Les codes personnalisés adoptent le même flux de travail compatible Git que celui utilisé par d'autres entités JCB :

* **Init** – Importez les enregistrements de code personnalisé à partir d'un référentiel.
* **Réinitialiser** – Remplacez la définition locale par la version du référentiel.
* **Push** – Publiez des mises à jour lorsque vous disposez d'un accès en écriture.
* **Fork** – Conservez une variante personnelle ou spécifique à une équipe pendant que l'amont continue d'évoluer.

Cette approche modulaire encourage les équipes à partager des ensembles sélectionnés d'extraits réutilisables et de règles d'automatisation sur plusieurs projets.

---

<a id="5-where-to-go-next"></a>
## 5. Où aller ensuite

* [CONSEILS : Code personnalisé](https://git.vdm.dev/joomla/Component-Builder/wiki/TIPS:-Custom-Code) pour la référence de syntaxe des balises et les cas extrêmes.
* [Réutiliser le code personnalisé](./Reuse-Custom-Code.md) pour voir des modèles d'aide pratiques.
* [Importation automatique du code personnalisé pendant la compilation](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) pour les composants internes de l'automatisation du hachage.

Utilisez ces guides ensemble pour concevoir un flux de travail qui combine des extraits réutilisables et des remplacements sur disque sans perdre de travail entre les compilations.