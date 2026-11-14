> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-admin-views"></a>
# Vues de l'administrateur JCB

Les vues d'administration JCB sont au cœur de chaque composant généré par Joomla Component Builder. Ils transforment votre modèle de données en un
expérience d'administration Joomla entièrement fonctionnelle en compilant des tables de base de données, des contrôleurs CRUD, des mises en page de liste et de modification, une barre d'outils
des boutons, des règles ACL et même des widgets de tableau de bord facultatifs en un seul geste. Parce que le compilateur comprend la relation entre les vues d'administration et
champs, Dynamic Gets et ressources côté site, une vue unique bien structurée s'étend des prototypes rapides aux données de niveau entreprise
applications sans passe-partout manuel.

> 🧭 **Nouveau ici ?** Commencez par l'[index de documentation](../index.md) pour une carte de haut niveau, puis revenez à cette fonctionnalité en profondeur
> lorsque vous êtes prêt à modéliser des données.

<a id="why-admin-views-are-a-flagship-feature"></a>
## Pourquoi les vues d'administration sont une fonctionnalité phare

JCB accélère le développement de Joomla! en vous permettant de décrire une vue d'administration une seule fois et en laissant le compilateur faire le gros du travail. Le
les fonctionnalités qui en résultent incluent :

* **Schéma de base de données instantané** : chaque vue d'administration définit et gère sa structure de table avec une gestion des versions au niveau du champ.
* **Pile MVC générée** – répertorie et modifie les mises en page, les modèles, les contrôleurs, les actions par lots, les filtres et les barres d'outils compilées automatiquement.
* **Autorisations granulaires** – Les commutateurs Joomla ACL exposent un accès par vue et par champ, prêts pour la gouvernance d'entreprise.
* **Gestion des relations** : les sous-formulaires, les requêtes dynamiques, les filtres chaînés et la logique d'affichage conditionnelle connectent les vues d'administration sans
  SQL supplémentaire.
* **Actifs réutilisables** : les mises en page, les modèles, les espaces réservés de code personnalisé et les chaînes de langue se déplacent avec la vue afin que vous puissiez créer ou créer des fichiers.
  réinitialisez-les entre les projets.

Associez cet aperçu conceptuel à la procédure pas à pas détaillée dans le
[Transcription du didacticiel JCB Admin Views](../Admin-Views.md) chaque fois que vous souhaitez des horodatages, des captures d'écran ou des exemples plus approfondis.

<a id="when-to-create-an-admin-view"></a>
## Quand créer une vue administrateur

Créez une vue d'administration chaque fois que vous avez besoin de gérer des données structurées dans un composant : articles, configurations, catalogues ou tout autre
objet qui mérite des opérations CRUD. Les composants JCB ne seront pas compilés sans au moins une vue Admin, alors considérez-la comme la vue de départ.
point pour chaque projet. À partir de là, vous pouvez installer [Custom Admin Views](../Custom-Admin-Views.md) pour les tableaux de bord ou
[Site Views](../Adding-Site-Views-to-a-Component.md) pour l'interface publique, le tout alimenté par la même fondation de données.

<a id="prerequisites-checklist"></a>
## Liste de contrôle des prérequis

Avant de vous lancer dans le constructeur, assurez-vous de :

1. Comprenez comment [JCB Fields](../JCB-Fields.md) contrôle les colonnes de la base de données et les widgets de formulaire.
2. Planifiez votre structure de données à l'aide des conseils de [Planification générale](../General-Planning.md#12-admin-views-and-field-creation).
3. Installez ou mettez à jour JCB en suivant le [guide d'installation](../Installation-of-JCB.md) afin que les exemples de données et les bibliothèques de champs soient
   disponible.

<a id="step-by-step-building-your-first-admin-view"></a>
## Étape par étape : créer votre première vue d'administration

Suivez ces étapes pratiques pour créer une vue administrateur robuste. Chaque étape est conçue pour que même les nouveaux utilisateurs puissent produire un
écran backend professionnel Joomla dès leur première tentative.

1. **Ouvrez la zone Vues d'administration**
   1. Lancez Joomla Component Builder dans votre administrateur Joomla.
   2. Dans la barre latérale, choisissez **Vues administrateur → Nouveau**.
   3. Donnez à votre vue un **Nom unique** (singulier) et un **Nom pluriel** (étiquette de liste). Tenez-vous-en aux noms en minuscules et séparés par des traits de soulignement
      pour les alias de table prévisibles.
2. **Décrivez la vue**
   1. Ajoutez des descriptions courtes et longues pour aider les coéquipiers à comprendre l'objectif.
   2. Sélectionnez le **Type** : `Read/Write` pour les enregistrements modifiables ou `Read Only` pour les journaux d'audit et les tables de recherche.
   3. Attribuez une icône pour que la vue ressorte sur le tableau de bord des composants. Le
      [Ajout de vues d'administration à un guide de composants](../Adding-Admin-Views-to-a-Component.md#2-adding-view-icons) affiche les tailles recommandées.
3. **Joindre des champs**
   1. Accédez à l'onglet **Champs**.
   2. Cliquez sur **Ajouter un champ** et réutilisez les définitions de champs existantes ou créez-en de nouvelles à la volée.
   3. Réorganisez les champs par glisser-déposer pour regrouper les entrées associées. Référencez le
      [Présentation des types de champs](../Field-Types.md#7-admin-fields-and-views) pour les widgets appropriés.
4. **Relations modèles**
   1. Utilisez l'onglet **Vues liées** pour connecter des sous-formulaires ou des relations parent-enfant.
   2. Configurez les filtres de liste et le classement des champs relationnels pour rendre la navigation intuitive.
   3. Lorsque vous avez besoin de données agrégées, attachez des requêtes dynamiques en suivant les instructions
      [guide DynamicGet](../dynamicGet.md#overview).
5. **Affiner l'expérience**
   1. Activez l'historique des versions, les actions par lots, l'exportation/importation et les commutateurs de métadonnées dans l'onglet **Options**.
   2. Définissez les paramètres par défaut de Joomla ACL dans l'onglet **Autorisations** afin que les éditeurs, les gestionnaires et les administrateurs disposent du droit d'accès prêt à l'emploi.
   3. Déposez du CSS, du JavaScript ou du PHP personnalisé dans les espaces réservés fournis pour étendre le comportement sans pirater le code généré.
6. **Liez la vue à votre composant**
   1. Visitez **Composants → Votre composant → Vues d'administration** dans JCB.
   2. Basculez l'endroit où la vue doit apparaître (menu principal, module de tableau de bord, sous-menu, actions rapides).
   3. Compilez et installez le composant. Des captures d'écran détaillées en direct dans le
      [Procédure pas à pas de l'intégration de Admin View](../Adding-Admin-Views-to-a-Component.md).
7. **Tester et itérer**
   1. Ouvrez le composant compilé dans l'administrateur de Joomla pour ajouter des exemples d'enregistrements.
   2. Vérifiez que les filtres de liste, les autorisations et les boutons de la barre d'outils se comportent comme prévu.
   3. Si vous devez ajuster le schéma, mettez à jour la vue Admin et recompilez : JCB gère les migrations de bases de données via le
      [mise à jour SQL automatisée](../Auto-create-SQL-updates-for-Componets-in-JCB.md).

<a id="productivity-tips"></a>
## Conseils de productivité

* **Réutilisez les vues éprouvées** – Réinitialisez ou dupliquez les vues d'administration à partir de référentiels partagés afin que votre équipe démarre avec des schémas et une interface utilisateur audités.
  modèles.
* **Conserver la logique déclarative** – Tirez parti des conditions, des champs chaînés et des Gets dynamiques avant d'écrire du PHP personnalisé. Déclaratif
  les paramètres survivent aux régénérations et accélèrent l’intégration.
* **Choix de document** – Utilisez les champs de description et les messages de validation pour expliquer pourquoi chaque vue existe. Les futurs collaborateurs peuvent
  puis accédez directement à la fonctionnalité en utilisant les liens ci-dessus.

<a id="next-steps-and-related-learning"></a>
## Prochaines étapes et apprentissage associé

* Continuez avec [Vues d'administration personnalisées](../Custom-Admin-Views.md) pour créer des tableaux de bord qui consomment les mêmes données.
* Explorez [Configurer la vue Modifier le site](../Setup-Site-Edit-View-in-JCB.md) pour afficher vos données Admin View sur le frontend.
* Ajoutez l'[Index du répertoire des fonctionnalités](../Features/README.md) à vos favoris  une fois que des guides de fonctionnalités supplémentaires seront publiés (à venir).

Revenez à [index de la documentation principale](../index.md) chaque fois que vous avez besoin d'un autre sujet.