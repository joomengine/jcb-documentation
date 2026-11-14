> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="global-settings-of-joomla-component-builder-jcb"></a>
# Paramètres globaux de Joomla Component Builder (JCB)

Le panneau **Paramètres globaux** de Joomla Component Builder fournit les outils essentiels pour configurer le comportement de votre composant, gérer les enregistrements, gérer les autorisations et sécuriser les données.
L'accès à ces paramètres est disponible via le bouton **Options** dans le tableau de bord de Component Builder.

---

<a id="1-accessing-global-configurations"></a>
## 1. Accéder aux configurations globales

[00:00:00](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h00m00s)

1. Ouvrez le **Tableau de bord du générateur de composants**.
2. Cliquez sur le bouton **Options** dans la barre d'outils supérieure.
3. La fenêtre **Configurations globales** s'ouvrira.

Seuls les utilisateurs disposant des autorisations appropriées (généralement des super-utilisateurs ou des administrateurs) peuvent afficher et modifier ces options.
Si le bouton "Options" est manquant, ajustez les autorisations de votre groupe d'utilisateurs Joomla.

Dans la fenêtre de configuration, vous trouverez plusieurs onglets clés :

* **Mondial**
* **Paramètres UiKit**
* **Paramètres de cryptage**
* **Chemins des dossiers**
* **Autorisations**

---

<a id="2-check-in-timer"></a>
## 2. Minuterie d'enregistrement

[00:01:16](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h01m16s)

Le **minuteur d'enregistrement** détermine la durée pendant laquelle un élément reste verrouillé lorsqu'un utilisateur l'extrait pour le modifier.
Une fois le délai sélectionné écoulé, JCB réenregistre automatiquement l'article.

**Intervalles disponibles :**

* 5 heures
* 12 heures
* 24 heures
*Tous les deux jours
* Une fois par semaine
*Jamais

Un intervalle de 24 heures est généralement recommandé pour la plupart des workflows de développement.

---

<a id="3-enable-versioning"></a>
## 3. Activer la gestion des versions

[00:01:55](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h01m55s)

La gestion des versions permet à JCB de suivre et de stocker différentes versions d'un enregistrement.

* **Oui** - Active la gestion des versions.
* **Non** - Désactive la gestion des versions.
* **Nombre de versions à conserver** - Définissez un nombre maximum de versions (entrez `0` pour toutes les conserver).

Si votre composant est utilisé fréquemment ou stocke de grandes quantités de données, la limitation des versions stockées permet de maintenir les performances de la base de données.

---

<a id="4-minify-javascript-js"></a>
## 4. Réduire JavaScript (JS)

[00:02:25](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h02m25s)

JCB peut automatiquement compresser et réduire tous les fichiers JavaScript lors de la compilation du composant.

* **Oui** - Réduire les fichiers JS (recommandé pour les environnements de production).
* **Non** - Conservez les fichiers JS intacts (recommandé pour le développement).

Lorsque la minification est active, tous les actifs JS de votre composant compilé sont optimisés pour améliorer les performances de chargement.

---

<a id="5-contributor-information"></a>
## 5. Informations sur les contributeurs

[00:03:28](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h03m28s)

Dans cette section, vous pouvez ajouter les noms des développeurs ou contributeurs ayant travaillé sur le composant.
Ces noms apparaîtront sous la section **Contributeurs** du tableau de bord JCB.

Cette fonctionnalité aide à maintenir un crédit approprié et à suivre la collaboration de développement au sein des équipes.

---

<a id="6-uikit-settings"></a>
## 6. Paramètres UiKit

[00:03:37](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h03m37s)

UiKit est un framework front-end que JCB prend en charge en option dans le développement back-end et front-end.

Actuellement, UiKit est principalement implémenté dans des zones backend limitées.
Il est destiné à une utilisation future potentielle dans la structure des composants frontend de JCB (par exemple, lors de la création d'interfaces frontend ou de tableaux de bord).

Vous pouvez laisser ces paramètres inchangés en toute sécurité, sauf si vous travaillez spécifiquement avec la fonctionnalité frontale basée sur UiKit.

---

<a id="7-encryption-settings"></a>
## 7. Paramètres de cryptage

[00:04:44](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h04m44s)

Component Builder inclut des fonctionnalités de cryptage des données qui protègent les informations sensibles stockées dans la base de données.

Pour activer le cryptage :

1. Saisissez une **Clé de cryptage de base** dans le champ prévu à cet effet.
2. Enregistrez la configuration.

Remarques importantes :

* Une fois que vous avez défini la clé, ne la **changez ni ne la supprimez**.
* Si la clé est supprimée, les données cryptées deviendront définitivement inaccessibles.
* Conservez toujours cette clé en toute sécurité dans un emplacement hors ligne ou de sauvegarde.

Cette fonctionnalité améliore la sécurité globale des données stockées de votre composant.

---

<a id="8-folder-paths"></a>
## 8. Chemins d'accès aux dossiers

[00:05:42](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h05m42s)

Les chemins de dossiers permettent à JCB de savoir où stocker les fichiers de sauvegarde et de compilateur utilisés lors du développement des composants.

Actuellement, seuls les chemins de dossiers suivants doivent être utilisés :

* **Chemin du dossier de sauvegarde**
* **Chemin du dossier Git**

Les champs **Chemin du dossier personnalisé** et **Chemin du dossier du compilateur** sont des espaces réservés pour le développement futur et doivent rester vides ou inchangés.
Ceux-ci sont conçus pour déplacer les dossiers liés au compilateur en dehors du répertoire accessible sur le Web afin d'améliorer la sécurité, bien que cette fonctionnalité ne soit pas encore entièrement implémentée.

---

<a id="9-permissions"></a>
## 9. Autorisations

[00:06:50](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h06m50s)

JCB s'intègre au système de liste de contrôle d'accès (ACL) de Joomla, offrant une gestion étendue des autorisations pour vos composants.

Les versions modernes de Joomla (3.5 et ultérieures) ont introduit la sauvegarde basée sur Ajax, qui permet à JCB de mettre à jour les autorisations sans avoir besoin de recharger la page ou de sauvegarder manuellement la configuration complète.

<a id="available-global-permissions"></a>
### Autorisations globales disponibles

* Créer
* Supprimer
* Modifier
* Modifier l'état
* Modifier le propriétaire
* Modifier créé par
* Modifier la date de création

Vous pouvez également configurer des autorisations par vue pour :

* Vues d'administration
* Vues d'administration personnalisées
* Dynamique obtenir des vues

Si nécessaire, attribuez à des groupes spécifiques l'autorisation **Configurer les options uniquement**, leur permettant de gérer les paramètres de configuration sans accès complet au composant.

---

<a id="10-example-preacher-permissions"></a>
## 10. Exemple : autorisations du prédicateur

[00:10:05](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h10m05s)

La vue **Preacher** dans le composant *Sermon Distributor* est un exemple du fonctionnement des structures d'autorisation de JCB.

Dans JCB, vous pouvez définir si les autorisations utilisent :

* `view.edit` - pour créer un contrôle spécifique à une vue (par exemple, `preacher.edit`)
* `core.edit` - pour appliquer les règles globales d'édition/suppression de Joomla

Après avoir compilé et installé le composant, ouvrez **Options → Autorisations** dans Joomla pour confirmer que ces nouvelles règles d'autorisation apparaissent pour les vues concernées.

---

<a id="11-field-permission-switch"></a>
## 11. Changement d'autorisation sur le terrain

[00:12:30](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h12m30s)

Les autorisations au niveau des champs permettent un contrôle précis sur qui peut modifier des champs individuels.

Pour activer le contrôle au niveau du champ :

1. Accédez à l'onglet **Champs** de votre composant.
2. Sélectionnez un champ spécifique (par exemple, *Nom du prédicateur*).
3. Activez **Changement d'autorisations**.
4. Enregistrez et fermez.
5. Recompilez et installez le composant.

Après l'installation, une nouvelle entrée d'autorisation apparaît dans l'onglet **Autorisations** de Joomla (par exemple, *Preacher edit name*).
Cela vous permet d'accorder ou de restreindre les droits de modification à des groupes d'utilisateurs spécifiques.

Pour supprimer une autorisation au niveau du champ :

1. Retournez sur le terrain dans JCB.
2. Définissez **Commutateur d'autorisations** sur **Non**.
3. Recompilez et réinstallez le composant.

Les autorisations de champ peuvent être ajoutées ou supprimées à tout moment et compilées dans le composant selon les besoins.

---

<a id="summary"></a>
## Résumé

La zone **Paramètres globaux** de Joomla Component Builder offre aux développeurs un contrôle granulaire sur la façon dont les composants sont configurés, sur la manière dont les utilisateurs interagissent avec eux et sur la sécurité avec laquelle ils gèrent leurs données.

En comprenant et en configurant correctement ces options, en particulier la gestion des versions, le chiffrement et les autorisations, vous pouvez garantir que vos composants sont sécurisés, efficaces et structurés de manière professionnelle pour tout environnement de projet.

---
