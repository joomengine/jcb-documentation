> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="joomla-components-in-jcb"></a>
# Composants Joomla dans JCB

Comprendre comment Joomla Component Builder (JCB) traite un **composant** rend le reste de la chaîne d'outils plus facile à suivre. Cette présentation explique le rôle d'un composant, les ressources qu'il rassemble et comment il ancre les flux de travail de collaboration.

---

<a id="what-is-a-jcb-component"></a>
## Qu'est-ce qu'un composant JCB ?

Un composant est le **bundle de premier niveau** que JCB compile dans une extension Joomla installable. Il agit comme un conteneur central qui connecte chaque entité que vous configurez ailleurs dans le générateur.

Un composant peut inclure :

- **Vues d'administration** : tables de données, formulaires d'édition, règles ACL et actions de la barre d'outils qui alimentent l'expérience backend ; revoir le
  [JCB Admin Views propose une analyse approfondie](./Features/JCB-Admin-Views.md) pour voir comment ils accélèrent les builds.
- **Vues du site** – présentations de listes et d'éléments expédiées vers le frontend.
- **Vues d'administration personnalisées** – écrans de gestion sur mesure situés à l'extérieur de l'échafaudage CRUD.
- **Modules et plugins** – extensions facultatives fournies avec le composant principal ; voir les [Modules JCB Joomla](./Joomla-Modules.md) pour les flux de travail spécifiques aux modules et les notes sur les [Plugins JCB Joomla](./Joomla-Plugins.md) pour la logique événementielle.
- **Code personnalisé** – méthodes d'assistance, remplacements de classe et extraits réutilisables injectés dans la sortie générée.
- **Fichiers et dossiers** – ressources multimédias, scripts, modules linguistiques ou autres ressources qui doivent être copiées dans le système de fichiers de Joomla.
- **Ajustements de base de données** – mises à jour de schéma, installation/mise à niveau de SQL et données de démonstration.
- **Classes d'assistance** – utilitaires PHP que d'autres parties du composant peuvent appeler.
- **Configuration globale** – les paramètres XML qui apparaissent dans l'écran des options des composants de Joomla.
- **Espaces réservés et remplacements** – remplacements automatisés et remplacements de mise en page pour garder le code au sec.
- **Tableaux de bord** – écrans de présentation dynamiques pour les administrateurs.
- **Règles de routage** – définitions de routage du site et de l'administrateur.
- **Version cibles** – Paramètres de compatibilité Joomla 3/4/5 et instructions d'emballage.
- **Actifs de documentation** : fichiers README, wikis, journaux de modifications ou métadonnées de paternité qui aident les coéquipiers à s'orienter.

Lorsque vous compilez, JCB assemble ces pièces mobiles dans un seul package versionné. Toutes les autres entités que vous créez dans JCB appartiennent finalement à un ou plusieurs composants.

---

<a id="why-components-are-central"></a>
## Pourquoi les composants sont centraux

Les composants définissent les limites de votre extension Joomla. Au sein d'un composant, vous décidez :

- **Packaging** – quelles vues, modules, plugins et assistants sont installés ensemble.
- **Cycle de vie de la base de données** : comment les tables sont installées, migrées et amorcées.
- **Disposition du système de fichiers** – où les actifs atterrissent lors de l'installation.
- **Compatibilité** – quelles versions et branches Joomla sont prises en charge par le package.
- **Flux de distribution** : serveurs de mise à jour, journaux des modifications, gestion des versions et métadonnées de paternité.
- **Couverture linguistique** – quels fichiers de langue et remplacements de traduction sont inclus.
- **Détails de la collaboration** – Liens vers le référentiel Git, informations sur l'auteur et notes qui aident une équipe à coordonner son travail.

> Considérez le composant comme votre **source unique de vérité**. Les champs, les vues, les mises en page et les extraits de code ne deviennent une extension cohérente qu'une fois que vous les liez à un composant et que vous les compilez.

---

<a id="version-control-and-collaboration"></a>
## Contrôle de version et collaboration

Les composants participent pleinement aux outils de synchronisation de JCB :

- **La configuration compatible avec les branches** vous permet de préparer différentes sorties pour Joomla 3, 4 ou 5.
- **Les workflows de réinitialisation et d'initialisation** aident les équipes à cloner les configurations de base et à maintenir les forks alignés.
- La **gestion des versions au niveau des composants** enregistre les entrées du journal des modifications afin que vous puissiez suivre ce qui a changé entre les versions.
- **Le forking et le partage** facilitent la maintenance de variantes en marque blanche ou d'éditions communautaires à partir de la même définition source.
- Les **pousses de mise à jour** permettent aux responsables d'envoyer des améliorations en amont ou de les distribuer sur des référentiels partagés.

Étant donné que les composants encapsulent toutes les dépendances, ils sont idéaux pour les équipes distribuées, les projets clients et les versions open source.

---

<a id="what-to-read-next"></a>
## Que lire ensuite

Utilisez cette page comme plate-forme avant de plonger dans les didacticiels plus approfondis :

- [Structure des composants et implémentation MVC](./Component-Structure-and-MVC-Implementation.md) – mappez le code généré à l'architecture de Joomla.
- [Présentation des paramètres des composants](./Component-Settings-Overview.md) – comprend les options globales, les cibles de version et les métadonnées d'empaquetage.
- [Ajout de vues d'administration à un composant](./Adding-Admin-Views-to-a-Component.md) – définissez les tables de données et les écrans back-end qui se trouvent à l'intérieur de votre composant.
- [Ajout de vues de site à un composant](./Adding-Site-Views-to-a-Component.md) – affiche les données sur le frontend une fois la structure du composant en place.
- [JCB Joomla Modules](./Joomla-Modules.md) – planifiez des widgets réutilisables qui se trouvent dans les positions des modules tout en restant versionnés avec le composant.
- [JCB Joomla Plugins](./Joomla-Plugins.md) – documentez comment l'automatisation en arrière-plan et les écouteurs d'événements voyagent avec le composant lors de chaque compilation.
- [JCB Packaging Engine](./JCB-Packaging-Engine.md) – découvrez comment JCB crée l'archive installable après avoir configuré votre composant.

---

<a id="index-of-component-related-topics"></a>
## Index des sujets liés aux composants

- [Ajout de vues d'administration personnalisées à un composant](./Adding-Custom-Admin-Views-to-a-Component.md)
- [Scripts de composants](./Component-Scripts.md)
- [Paramètres des composants](./Component-Settings.md)
- [Développer un composant Joomla](./Develop-a-Joomla-Component---Guide-to-use-the-Component-Builder.md)
- [Développement avec Joomla Component Builder](./Developing-with-Joomla-Component-Builder.md)
- [Concept d'inclusion dynamique de fichiers et de dossiers](./Dynamic-File-and-Folder-Inclusion-concept.md)
- [Paramètres globaux du générateur de composants](./Global-Settings-of-Component-Builder.md)
- [Flux de travail collaboratif proposé dans JCB](./Proposed-Collaborative-Workflow-in-JCB.md)

Ajoutez cette référence à vos favoris chaque fois que vous avez besoin d'expliquer ce que « un composant » signifie au sein de JCB à vos coéquipiers ou à vos clients.