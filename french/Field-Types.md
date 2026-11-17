> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="field-types-in-joomla-component-builder"></a>
# Types de champs dans le générateur de composants Joomla

<a id="video-tutorialhttpsyoutubeohlzvthdxls"></a>
### [Tutoriel vidéo](https://youtu.be/OhLzvThDXls)

*Utilisez les liens d'horodatage pour accéder aux sections pertinentes.*

---

<a id="1-overview"></a>
## 1. Aperçu

Joomla! Component Builder (JCB) génère des composants Joomla complets, notamment des définitions de formulaires XML, des modèles, des vues et des contrôleurs.
Comprendre les **types de champs** est essentiel, car ils déterminent quels éléments de formulaire sont affichés dans les vues d'administration et de site de votre composant. Associez ce chapitre à [JCB Fields](./JCB-Fields.md) pour voir comment les enregistrements de champs individuels consomment ces types de champs, définissent le schéma de base de données et restent versionnés via les référentiels.

Un **type de champ** définit le comportement et l'apparence d'un champ : par exemple, une zone de texte, une case à cocher, un sélecteur de date, une liste ou une saisie répétable.
Ceux-ci sont stockés au format XML et traités via l'API de Joomla pour restituer le formulaire de manière dynamique.

Au-delà des définitions locales, JCB s'intègre également aux **dépôts Field Type**. Les types de champs sont gérés séparément, tout comme
[packages](How-to-install-jcb-packages.md) et [extraits](General-overview-of-how-community-snippets-work.md) : pour que vous puissiez partager,
réutilisez-les et synchronisez-les sur des projets ou des équipes entières.

> **Concept clé :**
> Tous les champs existent dans les vues - soit **lister les vues** (pluriel) soit **modifier les vues** (unique).
> JCB les construit automatiquement lorsque vous les définissez dans votre composant.

---

<a id="11-field-type-repositories--global-syncing"></a>
## 1.1 Dépôts de types de champs et synchronisation globale

JCB est livré avec une prise en charge complète du référentiel pour les types de champs. Un référentiel central géré par la communauté conserve les informations canoniques.
définitions pour chaque type de champ utilisé dans les projets JCB. Le dépôt officiel réside à
[`joomengine/joomla-fieldtypes`](https://github.com/joomengine/joomla-fieldtypes) et contient les dernières versions de chaque cœur
type : allant de **Texte** et **Liste** à des types plus avancés tels que **ModalSelect**, **Repeatable** ou **DynamicCheckboxes**.

<a id="why-repositories-matter"></a>
### Pourquoi les référentiels sont importants

* **Réinitialisation globale** – Tout type de champ local peut être réinitialisé à la définition en amont directement à partir de l'interface graphique JCB à l'aide de la **Réinitialisation**.
  bouton. Cela garantit que les métadonnées, les attributs XML et les valeurs de démonstration correspondent à la version faisant autorité.
* **Amorçage du projet** – Lorsque vous initialisez une nouvelle installation JCB, vous pouvez immédiatement extraire chaque type de champ du fichier global.
  référentiel afin que le générateur de composants démarre avec la bibliothèque la plus à jour.
* **Collaboration** – Les équipes peuvent s'appuyer sur une source de vérité partagée. Les mises à jour effectuées dans un projet (et poussées vers le référentiel) peuvent
  être distribué à tous les autres projets via un pull.

<a id="repository-operations"></a>
### Opérations du référentiel

Les référentiels de types de champs prennent en charge le même flux de travail que les extraits de code et les packages :

| Actions | Descriptif |
| --- | --- |
| **Init** | Configurez une installation JCB locale pour suivre un référentiel de type champ (communautaire, organisationnel ou personnel). |
| **Tirez** | Importez ou actualisez tous les types de champs à partir du référentiel distant. Utilisez-le lors de la configuration d'un nouvel environnement ou lorsque de nouvelles versions sont publiées en amont. |
| **Pousser** | Publiez vos mises à jour locales dans le référentiel, ce qui est idéal lorsque vous créez une bibliothèque personnalisée pour votre organisation. |

Vous pouvez vous connecter au référentiel communautaire mondial ou pointer JCB vers une télécommande fork/alternative, vous offrant ainsi une autonomie totale sur le
définitions que vous distribuez.

> **Astuce :** Forkez le dépôt officiel si vous avez besoin de paramètres par défaut personnalisés tout en bénéficiant des améliorations en amont. Vous pouvez
> fusionnez les mises à jour dans votre fork chaque fois que de nouveaux types de champs sont publiés.

---

<a id="2-views-field-types-and-fields"></a>
## 2. Vues, ​​types de champs et champs

[01:05](https://youtu.be/OhLzvThDXls?t=65)

Lorsque vous créez ou modifiez un article Joomla, vous interagissez avec une **vue**.
Le paramètre `view=article` dans l'URL indique que vous travaillez dans la **vue article**.

Chaque élément du formulaire (comme le titre, l'alias ou la zone de l'éditeur) correspond à un **champ**.
Derrière chaque champ se trouve un **type de champ** qui définit son comportement.

Les types de champs Joomla courants incluent :

* **Texte** - Pour une saisie simple sur une seule ligne.
* **Éditeur** - Pour le contenu WYSIWYG.
* **Liste / Radio / Case à cocher** - Pour choix multiples ou bascules.
* **Utilisateur / Date / Balise / Zone de texte / Étiquette **, et plus encore.

Ceux-ci sont tous définis comme des **types de champs** dans Joomla et mappés dans votre composant JCB.

---

<a id="3-list-and-edit-views"></a>
## 3. Répertorier et modifier les vues

[01:57](https://youtu.be/OhLzvThDXls?t=117)

Dans Joomla :

* La **Vue Liste** affiche un tableau d'éléments (par exemple, une liste d'articles).
* La **Modifier la vue** (ou la vue unique) s'ouvre lorsque vous cliquez sur un élément pour le modifier.

JCB crée automatiquement des vues de liste et d'édition pour chaque ensemble de données que vous définissez dans votre composant.
Chaque vue comprend des champs mappés à la vue, de sorte que les champs que vous définissez dans JCB sont rendus correctement une fois compilés.

---

<a id="4-all-fields-live-in-views"></a>
## 4. Tous les champs vivent dans les vues

Même si une vue de liste ressemble à un tableau, elle contient toujours des **champs** - par exemple :

* Le champ de recherche, les filtres et les colonnes du tableau sont tous techniquement des **champs**.
* La vue d'édition affiche des champs de saisie individuels, regroupés en onglets ou sections.

Chez JCB :

* Vous définissez des champs dans une vue.
* Une fois compilé, JCB utilise la syntaxe XML du formulaire Joomla pour créer automatiquement la mise en page du formulaire.

> **Conseil :**
> L'ordre et le regroupement des champs peuvent être gérés directement dans l'interface JCB par glisser-déposer ou par onglets.

---

<a id="5-compiling-and-installing-your-component"></a>
## 5. Compilation et installation de votre composant

[05:45](https://youtu.be/OhLzvThDXls?t=345)

Lors de la compilation de votre composant dans JCB, assurez-vous de configurer correctement les **Paramètres globaux** :

* Assurez-vous que les options du référentiel Git sont définies (si vous utilisez le push automatique).
* Sinon, désélectionnez les actions du référentiel avant de compiler.

Si vous rencontrez un avertissement du type « Impossible de déplacer le fichier vers le référentiel Git », cela indique généralement que les chemins du référentiel ne sont pas définis – et non une véritable erreur de compilation.

[06:35](https://youtu.be/OhLzvThDXls?t=395)
Une fois compilé, cliquez sur **Installer** pour déployer le composant directement dans votre instance Joomla.
Le composant de démonstration s'installera avec succès, même s'il ne peut pas inclure d'images de démonstration.

---

<a id="6-exploring-the-jcb-demo-component"></a>
## 6. Explorer le composant de démonstration JCB

Le composant de démonstration démontre :

* **Liste des administrateurs et modifications des vues**
* **Champs répétables**
* **Boutons radio personnalisés et champs d'alias**
* **Fonctionnalités d'importation** (non standard dans les composants principaux de Joomla)

Pour une référence technique approfondie sur le composant de démonstration, consultez le
[Annexe Wiki JCB](https://github.com/vdm-io/Joomla-Component-Builder/wiki/Using-the-JCB-Demo-Component-While-Building-Your-Local-Development-System).

---

<a id="7-admin-fields-and-views"></a>
## 7. Champs et vues d'administration

[08:04](https://youtu.be/OhLzvThDXls?t=484)

Dans **Admin Views**, JCB affiche les champs mappés à cette vue.
Tu peux:

* **Modifiez les champs existants** directement dans l'éditeur de vue.
* **Ajoutez de nouveaux champs** à l'aide du bouton "Ajouter un champ".

Cette structure vous permet de gérer efficacement de nombreux champs sur plusieurs composants.
JCB stocke chaque définition de champ et la lie à la vue correspondante.

---

<a id="8-field-types-in-joomlas-core-library"></a>
## 8. Types de champs dans la bibliothèque principale de Joomla

[09:26](https://youtu.be/OhLzvThDXls?t=566)

Chaque type de champ Joomla correspond à des attributs XML spécifiques qui définissent sa structure et son comportement.
Des exemples d'attributs pour un champ de case à cocher peuvent inclure :

```xml
<field name="published" type="checkbox" default="1" label="Published" />
```

> **Important :**
> Sauf si vous créez ou étendez des types de champs, évitez de modifier les valeurs par défaut.
> JCB fournit déjà des mappages pour tous les types de champs courants.

---

<a id="9-adding-custom-field-types"></a>
## 9. Ajout de types de champs personnalisés

JCB permet aux développeurs de créer des **types de champs personnalisés** mappés à la bibliothèque de champs de Joomla.

<a id="example-use-cases"></a>
### Exemples de cas d'utilisation :

* Extension du champ répétable de Joomla.
* Ajout d'attributs ou de logiques personnalisés (par exemple, conditions "Afficher sur").

L'option **"Afficher sur"** contrôle la visibilité des champs en fonction d'autres valeurs de champ - une amélioration JCB en plus de la fonctionnalité native de Joomla.

> **Conseil de pro :**
> Lorsque vous ajoutez de nouveaux types de champs, respectez toujours les conventions de dénomination et de propriété standard de Joomla pour garantir la compatibilité.

---

<a id="10-using-joomla-standard-form-fields"></a>
## 10. Utilisation des champs de formulaire standard Joomla

[12:29](https://youtu.be/OhLzvThDXls?t=749)

Reportez-vous à la documentation de Joomla pour une liste complète des [types de champs de formulaire standard](https://docs.joomla.org/Standard_form_field_types).

Chaque type de champ comprend :

* **Tapez le nom** (par exemple, `checkbox`, `list`)
* **Attributs obligatoires/facultatifs**
* Exemple de structure XML

JCB mappe ces définitions directement dans vos formulaires de composants.

---

<a id="11-the-xml-structure-for-joomla-forms"></a>
## 11. La structure XML pour les formulaires Joomla

[14:05](https://youtu.be/OhLzvThDXls?t=845)

Lors de la définition des attributs dans un type de champ, JCB crée des chaînes XML que Joomla utilise pour afficher les formulaires.
Exemple:

```xml
<field name="title" type="text" label="Title" description="Enter a title" required="true" />
```

L'ajout de nouveaux attributs dans JCB les ajoute automatiquement à la chaîne XML utilisée lors de la compilation.

[14:45](https://youtu.be/OhLzvThDXls?t=885)
Chaque type de champ dans JCB indique quels **champs** l'utilisent - par exemple, plusieurs champs de texte peuvent partager la définition du type de champ "Texte".

---

<a id="12-example-joomla-xml-for-text-field"></a>
## 12. Exemple : XML Joomla pour le champ de texte

[15:15](https://youtu.be/OhLzvThDXls?t=915)

La représentation XML d'un champ de texte pourrait ressembler à ceci :

```xml
<field name="alias" type="text" label="Alias" description="Unique alias for the item" />
```

Cette structure est automatiquement générée par JCB lors de la compilation et stockée dans le fichier XML utilisé par l'API de formulaire de Joomla.

---

<a id="13-compiler-and-xml-generation"></a>
## 13. Compilateur et génération XML

[17:43](https://youtu.be/OhLzvThDXls?t=1063)

Lors de la compilation :

* JCB reformate les étiquettes en **chaînes traduisibles**.
* Ajoute des métadonnées telles que les références de ligne du compilateur et les sources de fichiers.
* Insère vos attributs de champ dans le contexte XML correct.

Cela signifie que même si vous modifiez légèrement les valeurs des attributs, JCB les interprète toujours correctement lors de la reconstruction du XML.

---

<a id="14-demo-data-and-field-value-population"></a>
## 14. Données de démonstration et population de valeurs de champ

Lorsque vous créez un nouveau champ dans JCB, les valeurs de démonstration (issues de la définition du type de champ) sont automatiquement pré-remplies.
Cela accélère la création de champs et garantit la cohérence XML.

Par exemple:

* La création d'un nouveau champ **texte** est renseigné avec des exemples d'attributs XML.
* Vous pouvez les modifier avant de les enregistrer ou les laisser par défaut.

---

<a id="15-best-practices"></a>
## 15. Meilleures pratiques

**Conserver les types de champs par défaut intacts.**
**Utilisez les conventions de dénomination Joomla.**
**Regroupez les champs logiquement dans les vues (onglets, sections).**
**Compilez souvent** pour détecter rapidement les erreurs XML ou de mappage.
**Utilisez les données de démonstration** pour comprendre la structure des champs avant de créer des types complexes.

---

<a id="16-conclusion"></a>
## 16. Conclusion

JCB automatise les mappages complexes XML, MVC et API Joomla! doit construire des composants robustes.
Les types de champs sont au cœur de ce processus : comprendre comment ils sont liés aux champs, aux vues et à la sortie XML vous aidera à concevoir des composants efficaces et évolutifs.

---
