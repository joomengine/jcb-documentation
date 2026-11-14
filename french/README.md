> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="start-here-onboarding-guide-for-joomla-component-builder"></a>
# Commencez ici : Guide de prise en main de Joomla Component Builder

<a id="what-this-page-does"></a>
## Que fait cette page

Joomla Component Builder (JCB) regroupe des années de connaissances de la communauté dans un seul ensemble de documentation. Cette page rassemble les liens et les concepts les plus importants afin qu'un nouveau venu puisse passer de « J'ai une expérience Joomla » à « Je peux livrer un composant JCB » sans se perdre dans la bibliothèque. Utilisez-le avec l'index [Accueil](./index.md) : Démarrer ici vous donne le chemin narratif, tandis que Accueil fournit une référence chapitre par chapitre.

---

<a id="step-1--understand-the-landscape"></a>
## Étape 1 – Comprendre le paysage

1. **Obtenez une vue d'ensemble d'un composant** afin de comprendre ce que JCB emballe finalement. [Composants Joomla dans JCB](./Joomla-Components.md) explique comment chaque vue, assistant, script et configuration se retrouve dans l'extension compilée.
2. **Consultez la structure MVC de Joomla** pour voir comment les applications d'administrateur et de site se reflètent, comment les contrôleurs, les modèles et les vues sont nommés et comment les packages sont assemblés. [Structure des composants et implémentation MVC](./Component-Structure-and-MVC-Implementation.md) comble le fossé entre la théorie de Joomla et l'automatisation de JCB.
3. **Clarifiez l'état d'esprit du workflow JCB** : ce que l'outil automatise, ce qui reste sous votre contrôle et comment les requêtes dynamiques agissent comme des requêtes de base de données conçues graphiquement qui alimentent vos vues. [Joomla Component Builder – Guide convivial pour les débutants](./Intro-to-JCB.md) résume les prérequis, les attentes de l'environnement et la boucle de construction globale, tandis que la mise à jour [Présentation de Dynamic Get](./dynamicGet.md#overview) explique comment le générateur de requêtes visuelles correspond aux modèles générés.
4. **Mappez la relation entre la base de données et l'interface** afin de savoir comment les vues d'administrateur, les vues de site et les champs se combinent pour fournir des données aux utilisateurs. Commencez par le nouveau [guide des champs JCB](./JCB-Fields.md) pour voir comment une définition de champ unique contrôle le stockage, le rendu, la validation et le partage. Utilisez ensuite [Planification générale](./General-Planning.md) et [Types de champs](./Field-Types.md) pour planifier des entités, choisir des types de champs et préparer la compilation, tandis que le guide actualisé [Ajout de vues de site](./Adding-Site-Views-to-a-Component.md) explique comment les requêtes dynamiques, les modèles, les mises en page, les blocs de code réutilisables et les bibliothèques assemblent l'expérience publique.

> 🧭 **Résultat :** vous devriez être capable de décrire les principaux répertoires Joomla, d'expliquer comment JCB les reflète et d'articuler les étapes de planification avant de toucher l'interface du constructeur.

---

<a id="step-2--prepare-your-toolchain"></a>
## Étape 2 – Préparez votre chaîne d'outils

1. **Configurez un environnement Joomla local** à l'aide de la chaîne d'outils OctoJoom, qui fournit pour vous les conteneurs Docker officiels de Joomla et Traefik. Suivez [Configurer un environnement de développement local avec OctoJoom](./Setup-Local-Development-Environment-with-OctoJoom.md) pour une procédure pas à pas ou répliquez manuellement les mêmes exigences conteneurisées.
2. **Installez Joomla Component Builder** à l'aide de la [procédure d'installation](./Installation-of-JCB.md) (package public unique, utilisation du compilateur, suppression des fichiers temporaires).
3. **Vérifiez les exigences PHP et du serveur** pour que la compilation réussisse. La [Référence des paramètres PHP](./PHP-Settings.md) répertorie les valeurs de configuration recommandées et les conseils de dépannage.  
4. **Importez des données de démonstration (facultatif)** pour explorer des exemples de travail. Le guide [Utilisation du composant de démonstration JCB](./Using-the-JCB-Demo-Component-While-Building-Your-Local-Development-System.md) explique comment le charger et l'inspecter.

> 🧭 **Résultat :** vous disposez d'un site Joomla fonctionnel avec JCB installé, des données de démonstration disponibles et la certitude que les paramètres du serveur ne bloqueront pas les builds.

---

<a id="step-3--build-your-first-component"></a>
## Étape 3 – Créez votre premier composant

1. **Commencez avec un exemple guidé :** suivez [Hello World with Joomla Component Builder](./Hello-World-with-Joomla-Component-Builder.md) pour créer un composant simple à partir de zéro, comprenant des vues d'administrateur et de site, des liens de menu et des autorisations.  
2. **Renforcez les fondations** en revisitant [Basic Fields](./Basic-Fields.md), [Admin Views](./Admin-Views.md) et [JCB Admin Views feature deep dive](./Features/JCB-Admin-Views.md) pour comprendre comment les champs remplissent les listes et les formulaires pendant que le générateur automatise le code MVC environnant.
3. **Entraînez-vous à la compilation et à l'installation** en effectuant de petites modifications, en recompilant et en réinstallant dans Joomla en suivant les instructions du didacticiel Hello World et de [Field Types](./Field-Types.md#5-compiling-and-installing-your-component).  
4. **Documentez votre apprentissage** : mettez à jour les notes des composants, suivez les noms des champs et tenez un journal des modifications. Cette habitude facilitera les tâches ultérieures d’exportation/importation ou de collaboration.

> 🧭 **Résultat :** vous pouvez créer un composant fonctionnel, le compiler, l'installer et reconnaître comment les données d'administration circulent vers l'interface du site.

---

<a id="step-4--explore-core-building-blocks"></a>
## Étape 4 – Explorez les éléments de base

| Concepts | Pourquoi c'est important | Ressources clés |
| --- | --- | --- |
| **Vues et champs de planification** | Traduire les exigences en tables de base de données, relations et autorisations. | [Planification générale](./General-Planning.md), [Guide des fonctionnalités des vues d'administration JCB](./Features/JCB-Admin-Views.md), [Ajout de vues d'administration](./Adding-Admin-Views-to-a-Component.md), [Ajout de vues de site](./Adding-Site-Views-to-a-Component.md) |
| **Composition et réutilisation de la vue du site** | Concevez des mises en page publiques en associant un Dynamic Get principal à des modèles, des mises en page, des espaces réservés de code personnalisés et des bibliothèques JS/CSS facultatives, puis gérez les mises à jour via des réinitialisations ou des forks. | [Ajout de vues de site](./Adding-Site-Views-to-a-Component.md), [Ajout de modèles et de mises en page](./Adding-Templates-and-Layouts-to-a-Site-View.md), [Mise en page JCB](./JCB-Layouts.md), [dynamicGet](./dynamicGet.md) |
| **Types de champs et validation** | Sélectionner les bonnes entrées et appliquer les données correctes. | [Champs JCB](./JCB-Fields.md), [Types de champs](./Field-Types.md), [Champs avancés](./Advanced-Fields.md), [Ajout d'une validation de règle](./Adding-your-own-rule-validation-to-a-field-in-JCB.md), [Règles de validation simples](./Easy-Validation-Rules-for-Fields-in-JCB.md) |
| **Récupération dynamique de données** | Combinaison d'enregistrements dans des tables sans SQL manuel. | [dynamicGet](./dynamicGet.md), [Ajouter DynamicGet à une vue de site](./Adding-dynamicGet-to-a-Site-View.md), [Importation automatique de code personnalisé](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) |
| **Modules et stages** | Expédiez des widgets réutilisables qui font apparaître les données des composants dans les positions des modules Joomla et maintenez-les synchronisés via les workflows Reset/Fork. | [Modules JCB Joomla](./Joomla-Modules.md) |
| **Modèles et mises en page** | Enveloppez les vues de site/administrateur avec des structures modulaires, des mises en page imbriquées et synchronisez le balisage réutilisable à partir de référentiels partagés. | [Modèles et mises en page](./Adding-Templates-and-Layouts-to-a-Site-View.md), [Configuration du modèle](./Template-Setup.md), [Configuration de la mise en page](./Layout-Setup.md) |
| **Code personnalisé et aides** | Extension des composants générés en toute sécurité grâce à des extraits de code tenant compte des arguments et à l'automatisation du hachage. | [Présentation des codes personnalisés JCB](./JCB-Custom-Codes.md), [Mise en œuvre manuelle du code personnalisé](./JCB-manual-custom-code-implementation.md), [Structures d'assistance](./Adding-Helper-Structures-to-any-JCB-component.md), [Méthodes d'assistance supplémentaires](./How-to-Add-More-Helper-Methods-to-Your-Components-Helper-Class.md) |

> 💡 **Rappel des Gets dynamiques :** traite chaque get principal comme la description canonique de la façon dont une vue obtient ses données. Le générateur visuel vous permet d'aligner les jointures, les filtres, le classement et le regroupement sans écrire de code SQL, et le code de modèle généré maintient le contrôle de version de ces règles aux côtés de vos modèles.

> 🧭 **Résultat :** vous savez où approfondir vos connaissances sur chaque pilier dès que votre projet l'exige.

---

<a id="step-5--choose-your-learning-pathway"></a>
## Étape 5 – Choisissez votre parcours d'apprentissage

<a id="1-project-planning--collaboration"></a>
### 1. Planification de projet et collaboration
- [Plongée approfondie sur les paramètres des composants](./Component-Settings.md)
- [Paramètres des composants](./Component-Settings-Overview.md)
- [Flux de travail collaboratif](./Proposed-Collaborative-Workflow-in-JCB.md)
- [Exporter/Importer des composants entièrement mappés](./Export-Import-of-fully-mapped-components.md)
- [Système de sauvegarde automatisé](./Automated-backup-system-in-JCB.md)

<a id="2-data-management--automation"></a>
### 2. Gestion et automatisation des données
- [Ajustement des données de démonstration MySQL](./Tweaking-MySQL-Demo-Data.md)
- [Créer automatiquement des mises à jour SQL](./Auto-create-SQL-updates-for-Componets-in-JCB.md)
- [Mises à jour automatisées de la base de données](./Automated-database-updates-in-Joomla-during-development-of-a-component.md)
- [Aperçu des codes personnalisés JCB](./JCB-Custom-Codes.md)
- [Réutiliser le code personnalisé](./Reuse-Custom-Code.md)

<a id="3-user-experience--site-delivery"></a>
### 3. Expérience utilisateur et livraison du site
Combinez des mises en page, des requêtes dynamiques, des bibliothèques JavaScript/CSS facultatives et des espaces réservés de code personnalisé réutilisables pour créer des expériences d'administrateur et d'interface raffinées qui reflètent votre modèle de données. Réinitialisez ou dupliquez les vues du site lorsque vous devez synchroniser avec des référentiels partagés ou maintenir des personnalisations à long terme.
- [Vues d'administration personnalisées](./Custom-Admin-Views.md)
- [Configurer la vue Modifier le site](./Setup-Site-Edit-View-in-JCB.md)
- [Quick Hello World (construction accélérée)](./The-Quick-Hello-Word-with-JCB.md)
- [Option de tableau de bord personnalisé](./The-custom-dashboard-option-in-JCB.md)

<a id="4-extensibility--ecosystem"></a>
### 4. Extensibilité et écosystème
- [Aperçu des extraits de communauté](./General-overview-of-how-community-snippets-work.md)
- [Remplacement de classe basé sur la puissance et injection de source](./Power-Based-Class-Overriding-and-Source-Injection.md)
-[Forking JCB Snippets](./Tutorial-on-forking-JCB-snippets-so-you-can-share-your-snippets-with-the-rest-of-the-Community.md)
- [Faire une demande d'extraction d'extrait](./Tutorial-on-making-a-pull-request-at-Joomla-Component-Builder-Snippets.md)
- [Moteur d'emballage JCB](./JCB-Packaging-Engine.md)
- [Publiez vos packages JCB](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md)
- [Suite de commandes CLI](./CLI-Command-Suite.md)

> 🧭 **Résultat :** choisissez le parcours qui correspond à l'étape immédiate de votre projet et suivez les didacticiels liés dans l'ordre.

---

<a id="step-6--maintain-and-scale-your-builds"></a>
## Étape 6 – Maintenez et faites évoluer vos builds

1. **Gestion de la configuration globale :** maîtrisez les paramètres au niveau des composants via [Paramètres globaux](./Global-Settings-of-Component-Builder.md) et découvrez comment les paramètres de menu interagissent dans [Gérer les options de configuration des composants](./Manage-a-Components-Global-Config-Option-Field-in-Relation-With-Menu-Params.md).  
2. **Déployez les mises à niveau en toute confiance :** étudiez la [Création automatique de mises à jour SQL](./Auto-create-SQL-updates-for-Componets-in-JCB.md) ainsi que les [Modifications du modèle de licence](./How-to-change-the-License-Template-in-JCB.md) pour automatiser les migrations de schémas et regrouper les métadonnées.  
3. **Gérer les traductions et la localisation :** combinez [Traduction facile via Excel](./Easy-Translation-via-excel.md) avec [Gestionnaire de traduction](./Translation-Mananger-in-JCB-explained.md) pour rationaliser le travail multilingue.  
4. **Surveillez les performances et la stabilité :** exploitez le [Système de sauvegarde automatisé](./Automated-backup-system-in-JCB.md) et le [Concept d'inclusion de fichiers dynamiques](./Dynamic-File-and-Folder-Inclusion-concept.md) pour que le code généré reste maintenable.

> 🧭 **Résultat :** vous disposez d'une liste de contrôle pour les tâches de maintenance à long terme qui vont au-delà de la première version.

---

<a id="how-to-navigate-the-documentation-efficiently"></a>
## Comment naviguer efficacement dans la documentation

- **Utilisez Démarrer ici + Accueil ensemble :** Démarrer ici vous oriente vers le bon sujet ; Accueil répertorie chaque chapitre avec des références chronologiques pour une analyse rapide.
- **Comprenez comment la documentation est produite :** [Développement avec Joomla Component Builder](./Developing-with-Joomla-Component-Builder.md) décrit le projet de transcription et donne des conseils pour étudier parallèlement aux vidéos.
- **Recherche dans le référentiel :** utilisez les outils de recherche ou de ligne de commande de votre éditeur (`rg "keyword" english/`) pour rechercher des fonctionnalités spécifiques, des noms de champs ou des références d'assistance dans les fichiers Markdown.  
- **Tirez parti de la barre latérale :** [`_Sidebar.md`](./_Sidebar.md) reflète l'index d'accueil et peut être épinglé dans les vues GitHub ou wiki pour une navigation persistante. Utilisez la nouvelle section **Fonctionnalités** pour accéder directement à des plongées approfondies comme [Vues d'administration JCB](./Features/JCB-Admin-Views.md).
- **Ajoutez le hub de fonctionnalités à vos favoris :** L'[index des fonctionnalités](./Features/README.md) répertorie toutes les fonctionnalités phares avec des liens vers des procédures pas à pas détaillées afin que vous puissiez informer rapidement vos coéquipiers.
- **Suivre l'état de révision :** les titres des chapitres incluent des notes de progression pendant que le projet d'édition est en cours. Donnez la priorité aux leçons entièrement éditées telles que [Types de champs](./Field-Types.md) lorsque vous avez besoin de conseils précis.  
- **Conservez des notes personnelles :** conservez un `docs/notes.md` ou un outil de suivi des problèmes dans le dépôt de votre projet pour enregistrer la façon dont vous avez appliqué les didacticiels : cela raccourcit la boucle de rétroaction lors du dépannage.

---

<a id="where-to-get-help-and-stay-updated"></a>
## Où obtenir de l'aide et rester informé

- **Discussions communautaires :** rejoignez les conversations en cours et posez des questions sur le [Tableau de discussion JCB](https://github.com/orgs/joomengine/discussions).
- **Playlist vidéo :** suivez la [playlist du didacticiel YouTube](https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE) complète  ainsi que les chapitres écrits.  
- **Mises à jour des tests bêta :** gardez un œil sur [Tests bêta](./Beta-Testing.md) pour les notes de version et les appels à testeurs.  
- **Contribuez en retour :** lorsque vous créez des aides, des mises en page ou des extraits de code, pensez à les partager via le flux de travail d'extraits de code ou le répertoire de packages lié ci-dessus.

> 🧭 **Résultat :** vous savez où poser des questions, regarder des démonstrations et contribuer aux améliorations à mesure que vous évoluez dans la plateforme.

---

<a id="ready-for-your-next-step"></a>
## Prêt pour votre prochaine étape ?

Revisitez cette page chaque fois que vous avez besoin de vous réorienter ou d’intégrer un coéquipier. Commencez par l'étape 1 si vous avez besoin d'un rappel sur l'architecture, passez à l'étape 4 pour explorer une fonctionnalité ou passez directement à l'étape 6 lors de la préparation d'une version. Bonne construction !