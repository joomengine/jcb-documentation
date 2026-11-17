> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-fields"></a>
# Champs JCB

Joomla Component Builder (JCB) s'articule autour des **champs**. Ils façonnent le schéma de votre base de données, pilotent les formulaires Joomla avec lesquels les administrateurs et les utilisateurs du site interagissent et coordonnent la manière dont les informations circulent dans chaque extension que vous compilez. Ce chapitre consolide les dernières instructions sur le comportement des champs, où ils sont utilisés et comment les maintenir maintenables dans les projets.

---

<a id="what-are-fields"></a>
## Que sont les champs ?

Les champs sont le **fondement** de chaque projet JCB. Chaque champ décrit simultanément vos données et la manière dont JCB doit les restituer, les valider et les conserver dans une extension compilée.

Une définition de champ est plus qu’une étiquette et un type d’entrée. Il contrôle le cycle de vie complet d'une valeur :

- **Structure de la base de données** – Définissez le moteur de stockage, le type, la longueur, les valeurs par défaut, la nullité, les contraintes uniques et les index que JCB doit créer lors de l'installation ou de la mise à niveau de votre composant.
- **Rendu** – Liez le champ à un type de champ pour que Joomla sache comment l'afficher : entrées classiques telles que `text`, `list` et `calendar`, mais aussi des expériences plus riches comme des sous-formulaires, des sélections modales ou des commutateurs à bascule.
- **Validation et autorisations** – Combinez les contrôles Joomla ACL, les indicateurs requis, les filtres et les règles de validation pour décider qui peut interagir avec la valeur et quels formats sont acceptés.
- **Intégration de modèles** – Étendre la sauvegarde et la récupération via des hooks PHP personnalisés (`onGet`, `onSave`, `onBeforeLoadForm`, etc.) sans créer de fichiers de base.
- **Détails de la présentation** – Configurez les classes, les attributs HTML, les scripts en ligne, les chaînes de langue et les remplacements de mise en page directement dans la définition du champ.

Étant donné que toutes ces décisions sont regroupées dans un seul enregistrement, le terrain devient une source unique de vérité que JCB peut réutiliser partout où les données apparaissent.

---

<a id="where-are-fields-used-in-jcb"></a>
## Où les champs sont-ils utilisés dans JCB ?

Les champs voyagent avec les structures qui les consomment. Une fois défini, un champ peut être mappé à :

- ✅ **Vues d'administration** – Les vues d'édition et de liste dans l'interface d'administrateur de Joomla.
- ✅ **Vues du site** – Formulaires frontaux et écrans de détail.
- ✅ **Modules** – Formulaires de configuration qui alimentent les positions des modules.
- ✅ **Plugins** – Intégrations basées sur des événements qui exposent les options du gestionnaire de plugins.
- ✅ **Configurations des composants** – Paramètres globaux disponibles via le panneau d'options des composants de Joomla.

JCB assemble automatiquement les intégrations XML, chaînes de langage et PHP appropriées pour chaque contexte afin que vous n'ayez pas besoin de dupliquer les définitions manuellement.

---

<a id="what-can-a-field-do"></a>
## Que peut faire un champ ?

Un seul enregistrement de champ dans JCB peut demander au compilateur de :

- Générez des définitions de **schéma de base de données** pour le SQL du programme d'installation et les mises à jour incrémentielles (`int`, `varchar`, `json`, types personnalisés, indicateurs nullables, index, etc.).
- Appliquez les **autorisations** en mappant les champs aux groupes ACL Joomla ou aux contrôles d'accès.
- Ajustez les **options de rendu** avec les classes HTML, les remplacements de mise en page, la logique d'affichage conditionnelle et les comportements JavaScript.
- Connectez-vous aux **événements de modèle** pour transformer les données avant l'enregistrement, après le chargement ou lors de la préparation du formulaire.
- Référencez des **types de champs** qui apportent des comportements avancés (sélections de modèles, sous-formulaires, commutateurs à bascule, champs chiffrés, etc.).

Cette centralisation rend la gestion sur le terrain efficace et hautement réutilisable. La planification d'un composant commence souvent par esquisser les champs et leurs relations. JCB articule ensuite le reste de la structure MVC autour de ces décisions.

---

<a id="reuse-sharing-and-versioning"></a>
## Réutilisation, partage et gestion de versions

Les champs sont des entités autonomes. Définissez-les une fois et mappez-les dans plusieurs vues d'administration, modules ou plugins selon vos besoins. Lorsque vous exportez ou partagez un composant, JCB regroupe chaque champ référencé afin que les collaborateurs reçoivent la même structure et le même comportement.

Vous contrôlez les mises à jour via le workflow compatible avec le référentiel de JCB :

1. Utilisez **Reset** dans l'interface utilisateur JCB pour synchroniser un champ avec la définition canonique stockée dans ce référentiel de documentation.
2. **Fork** le référentiel si vous avez besoin d'un comportement sur mesure, personnalisez le champ et pointez JCB vers votre fork.
3. Publiez ou importez des champs via des référentiels, tout comme des extraits de code et des packages, garantissant ainsi que les équipes restent alignées sans envoyer de dumps SQL par courrier électronique.

La gestion des versions dans Git conserve un historique complet de l'évolution de chaque champ, ce qui facilite les audits ou les restaurations.

---

<a id="field-workflow-at-a-glance"></a>
## Flux de travail sur le terrain en un coup d'œil

1. **Plan** – Identifiez les entités dont votre composant a besoin et capturez leurs attributs sous forme de champs. Utilisez [Planification générale](./General-Planning.md) pour obtenir des conseils sur le mappage des exigences aux tables de base de données.
2. **Créer** – Créez le champ dans JCB, en sélectionnant le type de champ, les paramètres de base de données, la validation et les options de présentation appropriés. Reportez-vous à [Champs de base](./Basic-Fields.md) pour une procédure pas à pas.
3. **Carte** – Attachez le champ aux vues d'administrateur, aux vues de site, aux modules ou aux plugins. [Vues administrateur](./Admin-Views.md) et [Ajout de vues de site](./Adding-Site-Views-to-a-Component.md) expliquent comment ces mappages affectent le code MVC généré.
4. **Compiler** – JCB génère des définitions, des modèles, des contrôleurs et un programme d'installation XML conformes à Joomla en fonction de votre configuration sur le terrain. Vérifiez le comportement en utilisant [Types de champs](./Field-Types.md) et [Champs avancés](./Advanced-Fields.md) comme références.
5. **Maintenir** – Lorsque des améliorations en amont arrivent, réinitialisez les champs du référentiel ou fusionnez les mises à jour de votre fork. Recompilez pour propager les modifications en toute sécurité.

---

<a id="extending-field-behavior"></a>
## Extension du comportement du champ

Parce que les champs se situent à l’intersection de la conception de bases de données et du rendu de formulaires, ils constituent l’endroit idéal pour centraliser la logique avancée :

- **Hooks PHP personnalisés** vous permettent de transformer des valeurs, de générer des données dérivées ou d'appeler des services externes pendant les opérations de sauvegarde et de chargement.
- Les **crochets de style** injectent des classes CSS ou des attributs en ligne qui alignent votre composant sur les systèmes de conception à l'échelle du site.
- Les **crochets de script** attachent des comportements JavaScript, permettant une amélioration progressive sans modifier les fichiers compilés.
- Les **valeurs dynamiques par défaut** peuvent rechercher des valeurs dans d'autres tables ou appliquer une logique contextuelle lors de la préparation du formulaire.

Utilisez ces fonctionnalités judicieusement afin que les champs restent réutilisables. Lorsque vous avez besoin d'une variante, créez un nouveau champ ou dupliquez l'entrée du référentiel plutôt que de surcharger une seule définition avec du code conditionnel.

---

<a id="keep-exploring"></a>
## Continuez à explorer

Utilisez ce chapitre comme point d’orientation, puis approfondissez des sujets spécialisés :

- [Champs de base](./Basic-Fields.md) – Créez des champs fondamentaux, configurez le stockage et inspectez la sortie compilée.
- [Champs avancés](./Advanced-Fields.md) – Explorez les relations de champs dynamiques, les structures répétables et les scripts personnalisés.
- [Types de champs](./Field-Types.md) – Comprendre l'architecture sous-jacente des types de champs Joomla et le flux de travail du référentiel.
- [JCB Fields Type Extended](./JCB-Fields-Type-Extended.md) – Parcourez des exemples avancés d'extension ou de remplacement de types de champs.
- [Valeurs de base de données par défaut par type de champ](./Default-Database-Values-can-be-set-per-Field-Type.md) – Automatisez les valeurs par défaut en fonction des définitions de type de champ.

> **Rappel :** Les champs définissent à la fois la structure et le comportement : c'est là que vos données prennent vie.

---

<a id="index-of-field-resources"></a>
## Index des ressources de terrain

| Sujet | Pourquoi c'est important | Chapitres clés |
| --- | --- | --- |
| Entités de planification et schéma | Traduisez les exigences en tables, relations et champs réutilisables. | [Planification générale](./General-Planning.md), [Vues administrateur](./Admin-Views.md) |
| Sélection des types de champs | Associez les champs avec le comportement de rendu et de stockage correct. | [Types de champs](./Field-Types.md), [Champs de base](./Basic-Fields.md) |
| Comportements avancés | Ajoutez des relations dynamiques, des sous-formulaires et des contrôles interactifs. | [Champs avancés](./Advanced-Fields.md), [Type de champs JCB étendu](./JCB-Fields-Type-Extended.md) |
| Validation et automatisation | Réutilisez les hooks PHP, les valeurs par défaut et les règles ACL dans toutes les vues. | [Règles de validation simples pour les champs](./Easy-Validation-Rules-for-Fields-in-JCB.md), [Valeurs de base de données par défaut par type de champ](./Default-Database-Values-can-be-set-per-Field-Type.md) |
| Partage et versionnage | Gardez les équipes alignées en synchronisant les bibliothèques de terrain réutilisables. | [Flux de travail collaboratif proposé](./Proposed-Collaborative-Workflow-in-JCB.md), [Comment installer les packages JCB](./How-to-install-jcb-packages.md) |

Revenez à cet aperçu chaque fois que vous avez besoin d'expliquer comment les champs sous-tendent JCB ou lors de l'intégration de coéquipiers qui apprennent le flux de travail pour la première fois.