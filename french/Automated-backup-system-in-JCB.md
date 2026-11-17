> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="automated-backup-system-in-joomla-component-builder"></a>
# Système de sauvegarde automatisé dans Joomla Component Builder

**Vidéo didacticiel :** [Regarder sur YouTube](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
(*Cliquez sur les horodatages pour accéder aux segments vidéo*)

---

<a id="1-overview-of-the-automated-backup-feature"></a>
## 1. Présentation de la fonctionnalité de sauvegarde automatisée

[00:00:00](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h00m00s)

Le système de sauvegarde automatisé fait partie de l'**Extension API** de JCB, permettant des opérations via une requête URL, y compris la création d'une sauvegarde complète de vos composants JCB.

L'extension API introduit de nouvelles possibilités d'automatisation. La première fonctionnalité implémentée est la **sauvegarde automatisée**, qui permet d'exporter et de stocker en toute sécurité vos composants soit manuellement, soit via un CronJob.

> **Remarque :** La communauté de développement de JCB discute de fonctionnalités API supplémentaires sur GitHub.

---

<a id="2-the-backup-button-and-core-function"></a>
## 2. Le bouton de sauvegarde et la fonction principale

[00:01:07](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h01m07s)

JCB inclut déjà une fonction **d'exportation de composants**. Le système de sauvegarde étend cela en ajoutant l'automatisation.

* Un bouton **Sauvegarde** a été ajouté pour les déclencheurs manuels.
* Le même processus peut également s'exécuter automatiquement via un **CronJob**.

Lorsqu'il est déclenché, JCB :

1. Exporte tous vos composants (sauf ceux de la corbeille).
2. Les crypte.
3. Les stocke localement dans un dossier de sauvegarde.
4. Envoie par e-mail la clé de cryptage à votre adresse e-mail sécurisée configurée.

> Seuls les composants *publiés*, *non publiés* ou *archivés* sont inclus. Les éléments mis à la corbeille sont ignorés.

---

<a id="3-new-configuration-tabs-and-features"></a>
## 3. Nouveaux onglets et fonctionnalités de configuration

[00:02:40](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h02m40s)

Pour prendre en charge le système de sauvegarde, plusieurs nouveaux onglets de configuration ont été ajoutés dans **JCB > Options** :

* **Configuration de la messagerie**
* **Paramètres DKIM**
* **Travail Cron**
* **Utilisateur API**

Ces paramètres contrôlent la manière dont les sauvegardes sont créées, sécurisées et livrées.

---

<a id="4-api-user-setup"></a>
## 4. Configuration de l'utilisateur de l'API

[00:03:09](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h03m09s)

L'**Utilisateur API** est l'identité du compte utilisée pour autoriser le processus de sauvegarde automatisé.

* Lorsque vous déclenchez manuellement une sauvegarde, JCB vérifie les autorisations en fonction de l'utilisateur connecté.
* Lorsqu'il est automatisé via CronJob, il utilise l'utilisateur API configuré.

> **Meilleure pratique :**
> L'utilisateur de l'API doit disposer de **autorisations complètes** sur tous les composants, champs et vues de JCB.
> Cela empêche les sauvegardes partielles ou restreintes causées par les limites d'autorisation.

Les futures mises à jour de JCB pourraient étendre ce modèle d'autorisation basé sur l'utilisateur, garantissant un contrôle d'accès sécurisé même pour les tâches automatisées.

---

<a id="5-cronjob-configuration"></a>
## 5. Configuration de la tâche Cron

[00:06:17](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h06m17s)

Dans l'onglet **CronJob**, vous pouvez trouver des conseils pour configurer l'exécution automatique.

Le système prend en charge les requêtes `curl` et `wget`.

* Si votre serveur prend en charge `curl`, JCB l'utilise automatiquement.
* Dans le cas contraire, il revient à `wget`.

Si aucune des deux commandes ne fonctionne, vous pouvez appeler manuellement l'**URL CronJob** fournie sur votre serveur.

Lorsqu'il est déclenché avec succès :

* Un message de confirmation vert apparaît : "Sauvegarde terminée et e-mail envoyé."
* Cette sortie peut éventuellement être enregistrée dans les versions futures.

> **Conseil :** Si votre site utilise un pare-feu (par exemple, RSFirewall), vous devrez peut-être configurer la requête pour qu'elle se comporte comme une requête de navigateur normale. Reportez-vous aux discussions liées à StackOverflow pour les ajustements `curl`.

---

<a id="6-backup-folder-and-encryption-details"></a>
## 6. Dossier de sauvegarde et détails de cryptage

[00:08:36](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h08m36s)

Par défaut, les sauvegardes sont enregistrées dans un **dossier local**.
Les versions futures permettront le stockage à distance (par exemple, des serveurs FTP) pour une redondance améliorée.

> **Important :** Joomla ne crypte pas les champs de configuration par défaut. Stockez les informations sensibles (par exemple, les clés de sauvegarde) en toute sécurité.

---

<a id="7-email-delivery-of-backup-key"></a>
## 7. Envoi par e-mail de la clé de sauvegarde

[00:09:13](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h09m13s)

La clé de cryptage utilisée pour la sauvegarde est automatiquement envoyée par courrier électronique à l'adresse configurée.
Assurez-vous que cet e-mail est **sécurisé** et **accessible uniquement aux administrateurs de confiance**.

---

<a id="8-package-naming-and-retention-strategy"></a>
## 8. Stratégie de dénomination et de rétention des packages

[00:09:33](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h09m33s)

Les sauvegardes sont nommées dynamiquement à l'aide d'horodatages :

* Par défaut : écrase les sauvegardes quotidiennes.
* Ajouter des espaces réservés pour les heures : conserve les versions horaires.
* Ajouter des espaces réservés de minutes : conserve chaque instance de sauvegarde.

Cette convention de dénomination vous permet de gérer la fréquence de remplacement des anciennes sauvegardes.

---

<a id="9-mail-configuration-and-dkim"></a>
## 9. Configuration de la messagerie et DKIM

[00:10:13](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h10m13s)

Dans l'**onglet Configuration de la messagerie**, vous pouvez choisir entre :

* La **Configuration Global Mail** de Joomla, ou
* Une **configuration SMTP** personnalisée pour les e-mails de sauvegarde.

> Utilisez toujours **SMTP avec SSL/TLS** pour une transmission sécurisée des clés de sauvegarde.

<a id="dkim-support"></a>
### Prise en charge DKIM

[00:10:54](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h10m54s)
L'activation de **DKIM (DomainKeys Identified Mail)** ajoute une couche supplémentaire d'authenticité et de confiance à vos e-mails de sauvegarde sortants.

---

<a id="10-company-details"></a>
## 10. Détails de l'entreprise

[00:11:10](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h11m10s)

Remplissez **Détails de l'entreprise** sous la configuration globale de JCB.
Ces détails font partie des métadonnées de sauvegarde et apparaissent lors de la restauration du package.

Assurez-vous que les éléments suivants sont définis avant d'enregistrer :

* Informations sur l'entreprise
* Paramètres de la tâche Cron
* Chemin du dossier de sauvegarde
* Paramètres de messagerie
* Utilisateur API

---

<a id="11-setting-the-export-key"></a>
## 11. Définition de la clé d'exportation

[00:12:10](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h12m10s)

Avant d'exécuter une sauvegarde :

* Assurez-vous qu'au moins un composant dispose d'un ensemble **Export Key**.
* Si plusieurs composants incluent des clés, JCB les combine en une seule clé de chiffrement (hachée pour des raisons de sécurité).

La clé de chiffrement réelle (qui vous est envoyée par courrier électronique) est dérivée de ces clés de composants.

---

<a id="12-running-a-manual-backup"></a>
## 12. Exécution d'une sauvegarde manuelle

[00:13:07](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h13m07s)

Vous pouvez lancer une sauvegarde manuelle à l'aide du bouton **Sauvegarde**.
Une fois terminé, un message de confirmation apparaît.

Pour vérifier :

1. Vérifiez le dossier de sauvegarde du nouveau fichier ZIP.
2. Confirmez la réception de l'e-mail de la clé de cryptage.
3. Ouvrez le fichier ZIP pour vérifier que tous les fichiers attendus sont présents, y compris les dossiers personnalisés le cas échéant.

> **Conseil :** Utilisez toujours un compte de messagerie sécurisé avec SMTP compatible SSL/TLS pour recevoir la clé de cryptage.

---

<a id="13-testing-the-backup-and-restore-process"></a>
## 13. Test du processus de sauvegarde et de restauration

[00:15:35](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h15m35s)

Pour valider votre sauvegarde :

1. Supprimez un composant existant (déplacez-le vers la Corbeille et videz-le).
2. Go to **Import Components**.
3. Select the backup directory.
4. Cliquez sur **Obtenir le fichier**, puis sur **Continuer**.
5. Enter the **encryption key** from your email.
6. Procédez à l'importation.

Lors de l'import, JCB affiche :

* **Détails du propriétaire du package**
* **Composants importés**

Une fois terminé, le composant est restauré.

---

<a id="14-verifying-restoration"></a>
## 14. Vérification de la restauration

[00:17:40](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h17m40s)

Pour confirmer le succès :

1. Ouvrez le **Compilateur**.
2. Sélectionnez le composant restauré.
3. Compilez-le et installez-le.
4. Vérifiez que tous les champs, vues et paramètres sont intacts.

> Vous avez maintenant configuré, automatisé et testé avec succès le processus de sauvegarde et de restauration de JCB.

---
