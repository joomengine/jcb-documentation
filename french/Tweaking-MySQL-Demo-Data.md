> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="tweaking-mysql-demo-data-in-joomla-component-builder"></a>
# Ajustement des données de démonstration MySQL dans Joomla Component Builder

<a id="video-reference"></a>
### Référence vidéo

[00:00:00 - Regarder sur YouTube](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Cliquez sur les liens horaires dans ce document pour accéder directement aux sections de la vidéo.*)

---

<a id="overview"></a>
## Aperçu

Dans Joomla Component Builder (JCB), **MySQL Tweaks** offre un moyen flexible de contrôler quelles données de démonstration ou factices sont incluses lors de la compilation de votre composant.
Ceci est particulièrement utile lors de la maintenance de **plusieurs versions** du même composant, où certaines versions nécessitent des exemples de données et d'autres non.

Ce guide utilise l'exemple **"Modification d'un composant"** pour expliquer comment fonctionne le réglage MySQL, comment l'utiliser efficacement et quand l'ignorer.

---

<a id="1-accessing-the-mysql-tweaking-area"></a>
## 1. Accéder à la zone de réglage MySQL

[00:00:43](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m43s)

1. Ouvrez votre composant dans **Joomla Component Builder**.
2. Accédez à l'onglet **Paramètres**.
3. Localisez la zone de réglage **MySQL**.

<a id="what-it-does"></a>
### Ce qu'il fait

Si votre composant a **plusieurs versions** et que certaines d'entre elles incluent des données de démonstration liées à des vues ou des ensembles de données spécifiques, le réglage MySQL vous permet d'**inclure ou d'exclure** ces données par version.

Ce paramètre est particulièrement utile si vous avez lié votre vue à une **table de données factice** ou à une autre source de base de données.

> **Conseil :** Cette fonctionnalité n'est applicable que lorsqu'une **connexion à la base de données** a été établie entre la vue de votre composant et une source de données dans MySQL.

---

<a id="2-understanding-how-jcb-uses-mysql-connections"></a>
## 2. Comprendre comment JCB utilise les connexions MySQL

[00:01:07](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m07s)

Par exemple, si vous ouvrez l'une des vues internes de JCB, telles que **Field Types**, et que vous la connectez à MySQL :

* Sélectionnez **Oui** sous *Connexion MySQL*.
* Choisissez la table de base de données appropriée.
* JCB **extrairea automatiquement les données de type de champ** dans le **fichier de construction** de votre composant.

Cela garantit que toutes les définitions de données de votre composant sont systématiquement incluses dans la sortie compilée.

---

<a id="3-the-tweaking-feature-explained"></a>
## 3. La fonctionnalité de réglage expliquée

[00:01:33](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m33s)

JCB est livré avec des versions de démonstration dans lesquelles tous les types de champs ne sont pas disponibles par défaut.
Pour personnaliser ce comportement, utilisez la **fonctionnalité de réglage** dans les paramètres.

[00:01:57](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m57s)

Lorsque vous ouvrez cette fonctionnalité de réglage :

* Vous verrez plusieurs options configurables (par exemple, *Administrateur personnalisé*, *MySQL pour afficher la table*).
* Certaines valeurs peuvent être définies sur **"Non"**, ce qui signifie que les données sont exclues de la build.
* Si **MySQL** est activé dans une vue, cette section vous permet de spécifier **quels ID** de la base de données de cette vue doivent être inclus.

[00:02:19](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s)

Par exemple, dans une vue Administrateur, les ID `33` et `42` peuvent avoir été inclus dans la base de données.
Ceux-ci sont contrôlés directement via le réglage MySQL.

> **Contrôler l'inclusion des données :**
> Le système de réglage est **basé sur l'ID**, vous permettant de définir quels enregistrements sont regroupés dans votre composant.

---

<a id="4-working-with-id-based-tweaks"></a>
## 4. Travailler avec des ajustements basés sur l'ID

[00:02:46](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m46s)

Cette fonctionnalité vous offre un **contrôle précis** sur les données incluses par ID.

<a id="syntax-format"></a>
### Format de syntaxe

Vous pouvez spécifier des plages et des ID individuels dans une **liste délimitée par des virgules** :

```text
1,2,3,4,20,40=>90
```

Cet exemple comprend :

* ID `1`, `2`, `3`, `4`
* ID `20`
* Tous les identifiants de `40` à `90`

[00:03:15](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m15s)

Vous pouvez également mélanger des plages et des ID discrets, par exemple :

```text
1=>4, 23, 199, 597=>604, 682=>684
```

Cela facilite l'inclusion d'**ensembles de données spécifiques** sans gérer manuellement chaque enregistrement.

[00:04:08](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s)

Après avoir défini votre liste d'ID, activez **Include = Yes** pour activer le réglage.

---

<a id="5-when-to-ignore-the-mysql-tweaking-area"></a>
## 5. Quand ignorer la zone de réglage MySQL

[00:04:46](https://www.youtube.com/watch?v=wkSLZUEN-RE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m46s)

Si votre composant **n'inclut pas de données factices ou de démonstration**, il n'est pas nécessaire de configurer le réglage MySQL.
Cela n'aura aucun effet sur le résultat de votre build.

> **Ignorer les ajustements inutilisés :**
> Si aucune donnée n'a été sélectionnée ou connectée dans votre composant, cette fonctionnalité peut être ignorée en toute sécurité.

---

<a id="6-summary"></a>
## 6. Résumé

| Objectif | Descriptif |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Contrôler les données de démonstration** | Gérez les exemples de données ou les données de démonstration intégrées dans vos versions de composants.      |
| **Flexibilité des versions** | Excluez les données pour les versions de production et incluez-les pour les versions de démonstration ou de développement. |
| **Inclusion basée sur l'identité** | Incluez les enregistrements en répertoriant leurs ID de base de données ou en spécifiant des plages.           |
| **Fonctionnalité facultative** | Nécessaire uniquement si votre composant intègre des tables de données factices.                   |

---

<a id="key-takeaways"></a>
## Points clés à retenir

* Accédez au **tweak MySQL** dans le composant **Paramètres**.
* Connectez votre vue à MySQL si vous souhaitez inclure des données réelles ou de démonstration.
* Utilisez des **listes d'ID délimitées par des virgules** pour spécifier les entrées à inclure.
* Ignorez complètement cette étape si votre composant n'utilise pas de données de démonstration ou d'exemple.

> **Conseil de pro :**
> MySQL Tweaks est particulièrement puissant lorsqu'il est utilisé dans le **développement de composants multiversions**, vous aidant à maintenir une séparation claire des données entre les versions de production et de démonstration.

---
