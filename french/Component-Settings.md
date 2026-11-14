> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="component-settings-in-joomla-component-builder"></a>
# Paramètres des composants dans Joomla Component Builder

Joomla Component Builder (JCB) vous permet de décrire presque toutes les parties d'une extension sans quitter l'interface Web. La zone **Paramètres des composants** est l'endroit où vous assemblez des menus personnalisés, importez des fichiers sur mesure et exposez les options de configuration aux administrateurs et aux éléments de menu. Ce guide transforme la transcription originale en une référence que vous pouvez numériser et appliquer lors de la construction de vrais projets.

<a id="prerequisites"></a>
## Prérequis

Avant de travailler dans les paramètres des composants, assurez-vous d'avoir :

- Un composant créé dans JCB avec au moins une vue administrateur.
- Tout code personnalisé ou mise en page préparé dans le dossier `/custom` de votre installation JCB si vous envisagez d'importer des fichiers.
- Les noms de champs que vous souhaitez exposer globalement déjà créés sous **Fields**.

> Besoin d'un rappel sur ce qu'un composant contrôle ? Lisez [Composants Joomla dans JCB](./Joomla-Components.md) pour la liste complète des actifs qui se compilent ensemble.

<a id="navigating-the-component-settings-workspace"></a>
## Navigation dans l'espace de travail Paramètres des composants

Les paramètres des composants se composent de trois onglets à fort impact :

1. **Vues administrateur et vues du site :** connectez les vues que vous avez créées ailleurs dans JCB.
2. **Menus d'administration personnalisés :** créez des entrées de menu d'administrateur supplémentaires qui pointent vers des contrôleurs personnalisés ou des liens externes.
3. **Config :** expose les paramètres à l'échelle du composant (et, lorsque la convention est suivie, leur menu remplace).

Chaque onglet fonctionne ensemble. Les menus personnalisés chargent généralement le code que vous avez importé via l'onglet **Fichiers**, et les champs de configuration doivent déjà exister sous **Champs** avant que vous puissiez les attribuer ici.

<a id="building-custom-administrator-menus"></a>
## Création de menus d'administrateur personnalisés

Utilisez les **Menus d'administration personnalisés** lorsque vous souhaitez un élément de navigation supplémentaire qui n'est pas généré à partir d'une vue standard.

1. **Définissez l'élément de menu** – fournissez un titre, un nom de code interne, un lien externe facultatif et choisissez une icône.
2. **Choisissez l'emplacement** – décidez si le menu apparaît dans la navigation du composant principal ou en tant que sous-menu et choisissez son emplacement par rapport aux entrées existantes.
3. **Code de support du lien** – si le menu doit ouvrir une vue sur mesure, assurez-vous que les fichiers du contrôleur, du modèle et de la mise en page sont importés via l'onglet **Fichiers** (voir ci-dessous).

C'est ainsi que la vue du compilateur JCB elle-même est regroupée : ses fichiers de contrôleur, de modèle, de vue et d'assistance sont conservés dans un dossier `compiler` sous `/custom`, puis mappés dans `admin/views/compiler` au moment de la construction. Le menu personnalisé pointe simplement vers cette vue.

<a id="importing-custom-files-and-folders"></a>
## Importation de fichiers et de dossiers personnalisés

Parfois, vous avez besoin de fichiers que JCB ne génère pas automatiquement (par exemple, PHPExcel, un contrôleur sur mesure ou une mise en page). Utilisez l'onglet **Fichiers** du composant pour les importer.

1. Placez vos actifs dans le répertoire `custom` de votre installation JCB, en reflétant la structure de destination souhaitée (les dossiers sont autorisés).
2. Dans Paramètres du composant → **Fichiers**, mappez chaque actif ou dossier à son emplacement cible. Vous pouvez renommer le fichier de destination dans le cadre du mappage.
3. Lorsque le composant est compilé, JCB crée d'abord les dossiers de destination, puis met en place vos actifs personnalisés.

L'utilisation de dossiers permet de conserver les fichiers associés ensemble. Par exemple, la suppression d'un dossier `compiler` entier garantit que tous ses fichiers arrivent sous `admin/views/compiler` sans les répertorier un par un.

<a id="configuring-global-component-options"></a>
## Configuration des options globales des composants

L'onglet **Config** pilote l'écran Options de Joomla qui apparaît lorsque vous ouvrez votre composant et cliquez sur **Options**. Ces paramètres peuvent gérer les minuteries, la gestion des versions, les contributeurs, les autorisations et toutes les bascules personnalisées que vous créez.

<a id="create-the-underlying-fields-first"></a>
### Créez d'abord les champs sous-jacents

1. Accédez à **Champs** et créez les définitions de champs dont vous avez besoin (boutons radio, listes déroulantes, espaceurs, etc.).
2. Attribuez à chaque champ un **Nom du système** unique tel que `preachers_display` ou `categories_display`. La réutilisation des noms provoque des conflits lors de l'enregistrement des options.

<a id="add-fields-to-the-config-tab"></a>
### Ajouter des champs à l'onglet Config

- Pour chaque paramètre, sélectionnez le champ créé précédemment et attribuez-lui un **Nom d'onglet**. Les champs portant le même nom d'onglet sont regroupés dans le modal Options de Joomla dans l'ordre indiqué ici.
- Vous pouvez inclure des champs d'espacement pour améliorer la lisibilité. JCB reconnaît les noms d'espaceurs répétés et les réutilise en toute sécurité.
- Fournissez des valeurs par défaut lorsque vous souhaitez que les composants nouvellement installés soient livrés avec les paramètres recommandés. Ces valeurs par défaut sont écrites dans la base de données lors de l'installation.

<a id="automate-frontend-menu-overrides"></a>
### Automatiser les remplacements de menu frontend

JCB reflète automatiquement les onglets de configuration dans les paramètres du menu frontal lorsque vous suivez une convention simple :

1. Faites correspondre le nom de l'onglet Config au nom de la vue frontale (par exemple, un onglet appelé `Preachers` correspond à la vue de liste `preachers`).
2. Assurez-vous que la vue frontale est configurée pour générer des paramètres de menu (`Add as Menu` défini sur **Oui**). JCB crée ensuite une mise en page `default.xml` à côté de la vue avec les mêmes champs.
3. Dans le PHP de votre vue (`view.html.php` ou fichiers de mise en page), récupérez les paramètres à l'aide de `$params = $this->state->get('params');` ou `$app->getParams();` et respectez les choix de l'utilisateur. Joomla! revient automatiquement à la valeur globale lorsque l'élément de menu est défini sur **Utiliser Global**.

C'est ainsi que le composant de démonstration Seven Distributor expose des choix tels que « tableau », « grille » ou « liste » à la fois sur l'écran Options et sur chaque élément de menu.

<a id="advanced-tools-mysql-tweak"></a>
## Outils avancés : ajustement de MySQL

La zone **MySQL Tweak** est destinée aux scénarios de distribution complexes dans lesquels vous expédiez plusieurs éditions du même composant. Il vous permet d'inclure ou d'exclure des données de démonstration par version. La plupart des constructeurs peuvent l'ignorer jusqu'à ce qu'ils créent des packages séparés.

<a id="recommended-conventions"></a>
## Conventions recommandées

- Adoptez des préfixes cohérents (tels que `preachers_`, `categories_`) pour les champs de configuration associés afin d'éviter les collisions de noms.
- Conservez la documentation de support dans votre référentiel afin que les futurs responsables sachent pourquoi un champ existe.
- Testez chaque élément de menu personnalisé après la compilation pour confirmer que les fichiers inclus sont copiés à l'emplacement prévu.

<a id="related-resources"></a>
## Ressources associées

- [Aperçu des paramètres des composants](./Component-Settings-Overview.md) – orientation basée sur une capture d'écran pour la même interface.
- [Gérer le champ d'option de configuration globale d'un composant en relation avec les paramètres de menu](./Manage-a-Components-Global-Config-Option-Field-in-Relation-With-Menu-Params.md) – examen plus approfondi de la façon dont les remplacements de menu interagissent avec les options des composants.
- [Importation automatique du code personnalisé pendant la compilation](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) – stratégies de gestion des packages de code réutilisables.