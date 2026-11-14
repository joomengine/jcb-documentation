> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="jcb-joomla-plugins"></a>
# Plugins Joomla JCB

<a id="what-are-joomla-plugins"></a>
## Que sont les plugins Joomla ?
Les **plugins Joomla** créés dans JCB sont des extensions basées sur des événements qui vous permettent d'injecter une logique personnalisée à des points clés du cycle de vie des applications Joomla. Ils sont parfaits pour des scénarios tels que :

- Tâches de ligne de commande (CLI)
- Opérations cron planifiées
- Filtres d'authentification
- Transformations de données ou couches de validation
- Intégrations au niveau du système avec des services externes

Chaque plugin peut regrouper des classes PHP, des bibliothèques d'assistance, des chaînes de langage et le manifeste XML du plugin. JCB vous permet également de joindre des champs personnalisés afin que le plugin soit livré avec des paramètres de configuration qu'un responsable du site peut ajuster directement dans Joomla.

---

<a id="how-plugins-fit-into-your-component"></a>
## Comment les plugins s'intègrent dans votre composant
Lorsque vous liez un plugin à un composant dans JCB, ce plugin est compilé à chaque fois que le composant est construit. Le moteur de packaging automatiquement :

1. Collecte les fichiers du plugin, les classes d'assistance et les chaînes de langue.
2. Génère tous les champs de configuration que vous avez définis pour le plugin.
3. Expédie le plugin compilé avec votre package d'installation de composant.

Ce couplage étroit signifie que vous pouvez garantir que l'automatisation en arrière-plan, les hooks d'authentification ou la logique de synchronisation des API sont distribués avec la version exacte du composant qui en a besoin, sans toucher aux fichiers principaux de Joomla.

> **Conseil :** Utilisez les paramètres du plugin pour exposer les commutateurs ou les informations d'identification qui doivent rester modifiables après le déploiement tout en conservant les détails d'implémentation dans le code compilé.

---

<a id="event-triggers-and-execution-contexts"></a>
## Déclencheurs d'événements et contextes d'exécution
Les plugins Joomla s'abonnent à des événements spécifiques (par exemple, `onUserLogin`, `onContentPrepare` ou rappels CLI). Au sein de JCB vous pouvez :

- Déclarez les événements que votre plugin doit écouter et implémentez les méthodes correspondantes.
- Décidez si le plugin doit s'exécuter dans l'application **site**, **administrateur** ou **CLI** en configurant le groupe et le contexte du plugin.
- Réutilisez les classes d'assistance partagées du composant, garantissant ainsi des règles métier cohérentes entre les points d'entrée Web et d'automatisation.

Étant donné que les plugins s'exécutent indépendamment des vues MVC de Joomla, vous pouvez placer la logique métier, les intégrations ou les tâches planifiées directement dans les écouteurs d'événements tout en laissant les contrôleurs de composants se concentrer sur la gestion des requêtes.

---

<a id="building-testing-and-shipping-plugins-in-jcb"></a>
## Création, test et expédition de plugins dans JCB

<a id="during-development"></a>
### Pendant le développement
- Commencez par échafauder le plugin dans JCB, puis ajoutez votre logique PHP et vos inclusions d'assistance.
- Utilisez le gestionnaire de champs de JCB pour définir les options de configuration qui apparaissent dans l'éditeur de plugin de Joomla.
- Déclenchez des événements de plugin localement à l'aide des outils de test de Joomla ou des points d'entrée CLI pour confirmer que la logique se comporte comme prévu.

<a id="at-compile-time"></a>
### Au moment de la compilation
- Incluez le plugin dans l'exportation de vos composants afin que chaque build soit livré avec une copie actuelle.
- Vérifiez que le manifeste XML du plugin généré répertorie tous les fichiers, chaînes de langue et champs de configuration.
- Vérifiez que les classes d'assistance référencées à la fois par le composant et le plugin sont correctement chargées automatiquement.

<a id="after-installation"></a>
### Après l'installation
- Activez le plugin depuis le gestionnaire de plugins de Joomla et ajustez tous les paramètres que vous avez exposés pendant le développement.
- Surveillez les journaux de Joomla ou la sortie CLI pour vérifier que vos écouteurs d'événements s'exécutent sans erreurs.

---

<a id="versioning-and-sharing"></a>
## Versionnement et partage
Lorsque vous devez mettre à jour les plugins Joomla dans n'importe quel projet JCB :

- Sélectionnez le(s) plugin(s) que vous souhaitez actualiser.
- Cliquez sur **"Réinitialiser"** pour extraire la dernière version de ce référentiel.
- Ou **Fork** ce référentiel et pointez votre instance JCB vers votre fork.

Cela garantit que vos plugins sont contrôlés en version et à jour, tout en permettant une personnalisation complète par projet.

> Les plugins sont un élément essentiel d'une architecture Joomla robuste, offrant des fonctionnalités silencieuses et pilotées en arrière-plan avec une intégration complète de JCB.

---

<a id="documentation-checklist"></a>
## Liste de contrôle de la documentation
Pour aider les collaborateurs à comprendre comment les plugins complètent un composant, assurez-vous que vos notes de projet incluent :

- Un résumé de chaque plugin, ses déclencheurs d'événements et le problème qu'il résout.
- Tous les paramètres de configuration, valeurs par défaut ou informations d'identification requises.
- Dépendances sur des classes d'assistance ou des services externes.
- Étapes de test (commandes CLI, fréquence cron ou flux utilisateur) qui exercent le plugin.

En gardant ces points à proximité de la documentation principale du composant, les nouveaux développeurs peuvent immédiatement voir comment l'automatisation et la logique événementielle accompagnent les fonctionnalités visibles de votre build.