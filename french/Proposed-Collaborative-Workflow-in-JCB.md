> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="proposed-collaborative-workflow-in-joomla-component-builder-jcb"></a>
# Flux de travail collaboratif proposé dans Joomla Component Builder (JCB)

Le moteur de packaging de JCB transforme chaque plan en un référentiel Git. Cela signifie que les équipes peuvent collaborer
sur les composants, les types de champs, les extraits de code et les pouvoirs avec la même discipline basée sur Git utilisée pour la source
code. Ce guide décrit un flux de travail pratique qui combine l'interface utilisateur de JCB avec les branches Git, pull
demandes et documentation du référentiel.

---

<a id="1-understand-jcbs-built-in-safeguards"></a>
## 1. Comprendre les garanties intégrées de JCB

JCB maintient le travail collaboratif prévisible avant même que Git n'entre en scène :

* **Check-in/check-out** – lorsqu'un utilisateur modifie un composant, JCB le verrouille jusqu'à ce qu'il enregistre et ferme le
  forme. Cela évite les modifications conflictuelles sur le même site Joomla.
* **Autorisations** – Les contrôles ACL de Joomla qui peuvent afficher, modifier ou gérer des types d'entités spécifiques à l'intérieur
  JCB. Configurez les autorisations sous *Composants → Générateur de composants → Options → Autorisations* pour correspondre
  les rôles de votre équipe.

Ces garde-fous sont toujours importants lorsque chaque développeur exécute une instance Joomla locale : ils garantissent
cohérence si plusieurs personnes se connectent au même site pour des solutions rapides ou des démos.

---

<a id="2-prefer-local-development-sync-through-git"></a>
## 2. Préférez le développement local, synchronisez via Git

La plupart des équipes exécutent JCB sur des conteneurs locaux, des machines virtuelles ou des serveurs de développement dédiés. Le travail local garde votre
Environnement Joomla rapide, jetable et isolé. Pour collaborer, les développeurs échangent le JCB
plans via le moteur de packaging au lieu de partager des sauvegardes de base de données ou des exportations ZIP.

> 🧠 **Astuce :** Automatisez la configuration locale (par exemple Docker + OctoJoom) afin que chaque développeur puisse recréer la même chose
> environnement avant d'importer les référentiels.

---

<a id="3-bootstrap-repositories-with-the-catalogue"></a>
## 3. Dépôts d'amorçage avec le catalogue

1. Enregistrez le référentiel `joomengine/repoindex` dans JCB (voir le
   [Guide du moteur d'emballage JCB](./JCB-Packaging-Engine.md)).
2. Utilisez **Init** dans la liste Dépôts pour cloner le catalogue et créer des entrées pour la démo officielle
   packages, bibliothèques de types de champs et référentiels d'assistance.
3. Pour chaque entité sur laquelle vous envisagez de collaborer, ouvrez-la et appuyez sur **Init** pour lier l'entité concernée.
   référentiels.

Chaque entrée du référentiel comprend une documentation expliquant le fonctionnement du plan, attendu
dépendances et notes de contribution.

---

<a id="4-learn-the-init--reset--push-cycle"></a>
## 4. Apprenez le cycle Init → Réinitialisation → Push

Une fois qu'un référentiel est lié à une entité :

* **Init** – importe le plan pour la première fois. Exécutez-le lors de l'intégration d'un nouveau développeur ou
  lorsque vous devez ajouter un plan du catalogue.
* **Réinitialiser** – extrait le dernier commit des référentiels publiés. Utilisez-le après la fusion d'un coéquipier
  une pull request pour que votre copie locale corresponde au référentiel canonique.
* **Push** – publie vos modifications locales sur Git. Assurez-vous que l'entrée du référentiel a une écriture
  succursale et des informations d’identification valides. Push affecte chaque référentiel publié pour ce contenu cible, donc
  dépublier toutes les destinations que vous ne souhaitez pas mettre à jour.

Les développeurs peuvent désormais collaborer en parallèle : chaque personne travaille localement, pousse jusqu'à son fork et ouvre
tirer des demandes de révision.

---

<a id="5-recommended-git-workflow"></a>
## 5. Flux de travail Git recommandé

1. **Fork** le référentiel en amont (par exemple `joomengine/packages`).
2. **Clonez** votre fork localement et enregistrez-le dans JCB avec des branches de lecture et d'écriture.
3. **Init** les entités concernées afin qu'elles pointent vers votre fork.
4. Apportez des modifications dans JCB, exécutez **Push** et validez les fichiers résultants.
5. Ouvrez une **demande d'extraction** sur le référentiel en amont décrivant la mise à jour et un lien vers n'importe quel
   questions ou discussions connexes.
6. Une fois fusionnés, les autres développeurs **Réinitialisent** leurs copies locales pour recevoir les modifications.

Étant donné que les référentiels sont simplement Git, vous pouvez créer des branches, baliser les versions, exécuter CI et examiner les différences avant
accepter les changements.

---

<a id="6-example-sharing-a-component-blueprint"></a>
## 6. Exemple : partage d'un plan de composant

Imaginez une équipe gérant un composant CRM complexe :

1. Le responsable technique crée `joomengine/packages`, crée `acme-crm` et documente les dépendances sur les
   types de champs.
2. Chaque développeur enregistre le fork dans son installation JCB, appuie sur **Init** et importe le
   composant.
3. Les développeurs travaillent sur des fonctionnalités distinctes dans JCB. Lorsqu'ils sont prêts, ils **Poussent** vers leur fork, s'engagent et
   ouvrir une pull request.
4. Le réviseur teste la modification en extrayant la branche localement, en exécutant **Reset** et en compilant le fichier.
   composant.
5. Une fois la pull request fusionnée, tout le monde exécute **Reset** pour synchroniser ses plans locaux et
   poursuit son développement.

Cela reflète les workflows Git conventionnels tout en laissant JCB gérer la résolution des dépendances et l'ID.
remapping dans les coulisses.

---

<a id="7-optional-remote-synchronisation"></a>
## 7. Facultatif : synchronisation à distance

La fonctionnalité **Serveurs** (intégrations SFTP) peut mettre en miroir des référentiels entre des installations JCB distantes.
Utilisez-le lorsque vous avez besoin d'un serveur intermédiaire central pour consolider le travail de plusieurs équipes. Même avec SFTP
synchronisez, conservez les référentiels Git comme source de vérité – ils fournissent un historique, des outils de révision et des fonctionnalités plus sûres.
reculs.

---

<a id="8-keep-security-in-mind"></a>
## 8. Gardez la sécurité à l'esprit

* Stockez les jetons GitHub en toute sécurité à l'aide des options cryptées de JCB.
* Limiter l'accès en écriture au référentiel aux utilisateurs de confiance.
* Examinez attentivement les demandes d'extraction, en particulier lorsqu'elles ajoutent des super pouvoirs ou des extraits qui exécutent PHP.
* Documentez les procédures de déploiement dans le référentiel README afin que les nouveaux contributeurs suivent les mêmes étapes.

---

<a id="9-additional-resources"></a>
## 9. Ressources supplémentaires

* [Moteur d'emballage JCB](./JCB-Packaging-Engine.md)
* [Publiez vos packages JCB](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md)
* [Importer des packages JCB](./How-to-install-jcb-packages.md)
* [Système de sauvegarde automatisé](./Automated-backup-system-in-JCB.md)

L'adoption du moteur d'emballage garantit la transparence, la révision et la facilité de partage de vos projets JCB.
sur plusieurs instances Joomla.