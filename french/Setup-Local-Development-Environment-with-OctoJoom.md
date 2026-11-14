> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="setup-local-development-environment-with-octojoom"></a>
# Configurer un environnement de développement local avec OctoJoom

> **Référence vidéo :** [Présentation d'OctoJoom](https://www.youtube.com/watch?v=owpxKie0I7s)
> **Documentation du projet :** [git.vdm.dev/octoleo/octojoom](https://git.vdm.dev/octoleo/octojoom)

OctoJoom est un script shell qui provisionne Joomla! en utilisant les images Docker officielles, Traefik comme proxy inverse et les fichiers Docker Compose générés pour vous. Il remplace l'ancienne approche basée sur Bitnami par un flux de travail reproductible et évolutif qui reflète la façon dont nous construisons des projets aujourd'hui. OctoJoom maintient chaque site local isolé tout en vous permettant d'exécuter plusieurs installations Joomla à la fois, ce qui est parfait pour travailler sur plusieurs projets JCB.

---

<a id="1-why-octojoom"></a>
## 1. Pourquoi OctoJoom ?

OctoJoom automatise les tâches de routine d'amorçage et de maintenance de votre pile de développement :

* **Conteneurs Joomla officiels** – chaque projet s'exécute sur les images gérées par l'équipe Joomla.
* **Routage optimisé par Traefik** : les noms de domaine conviviaux sont automatiquement mappés aux bons conteneurs.
* **Variables d'environnement réutilisables** – OctoJoom écrit des fichiers `.env` pour Docker Compose et Traefik, vous invitant uniquement lorsque des valeurs sont manquantes.
* **Flux de travail axé sur les tâches** : des commandes telles que `setup`, `enable`, `disable` ou `update` simplifient les opérations quotidiennes.
* **Convivial pour plusieurs sites** – lancez et gérez n'importe quel nombre de projets Joomla sur le même poste de travail sans conflits de ports.
* **Multiplateforme** – fonctionne sur les distributions Linux et macOS. Les utilisateurs Windows peuvent l'exécuter sur une machine virtuelle Ubuntu (ou similaire).

> **Astuce :** OctoJoom est doté de ShellCheck et conçu pour une utilisation sur terminal. Si vous omettez les options CLI, le script rassemble de manière interactive les détails requis.

---

<a id="2-prerequisites"></a>
## 2. Prérequis

Assurez-vous que les éléments suivants sont disponibles sur votre poste de travail avant d'installer OctoJoom :

1. **Système d'exploitation** – Ubuntu/Debian ou macOS. (Utilisez une machine virtuelle Linux lors du développement à partir de Windows.)
2. **Plugin Docker Engine et Docker Compose** – installez à partir du gestionnaire de packages de votre système d'exploitation ou des instructions officielles de Docker.
3. **Exigences Traefik** – OctoJoom configure Traefik pour vous, mais assurez-vous que le port 80 (HTTP) est libre. Si un autre serveur Web s'exécute localement, arrêtez-le avant de démarrer les sites gérés par OctoJoom.
4. **Résolution du nom d'hôte** : ajoutez des domaines de projet à `/etc/hosts` (par exemple, `127.0.0.1 jcb.test`) si vous n'utilisez pas de solution DNS locale.

---

<a id="3-install-octojoom"></a>
## 3. Installez OctoJoom

Installez le script globalement pour pouvoir exécuter `octojoom` depuis n'importe quel terminal :

```bash
sudo curl -L "https://raw.githubusercontent.com/octoleo/octojoom/refs/heads/master/src/octojoom" -o /usr/local/bin/octojoom
sudo chmod +x /usr/local/bin/octojoom
```

Mettre à jour plus tard avec :

```bash
octojoom --update --access-token <your_git_vdm_access_token>
```

Vous pouvez désinstaller à tout moment :

```bash
octojoom --uninstall
```

---

<a id="4-explore-the-help-menu"></a>
## 4. Explorez le menu Aide

Exécutez la commande d'aide pour examiner tous les commutateurs :

```bash
octojoom --help
```

Options clés que vous utiliserez fréquemment :

* `--type` – précisez ce avec quoi vous travaillez (`joomla` ou `openssh`).
* `--task` – choisissez l'action (`setup`, `enable`, `disable`, `update`, etc.).
* `--domain` / `--sub-domain` – définissez les noms d'hôtes que Traefik acheminera.
* `--key` – étiquette utilisée pour les noms de projets Docker Compose.
* `--env-key` – préfixe majuscule utilisé lorsqu'OctoJoom écrit des variables d'environnement.
* `--joomla-version` – choisissez la balise Joomla à extraire (par défaut, la dernière version stable si elle est omise).

Si vous ignorez un indicateur, OctoJoom demande la valeur de manière interactive et la stocke dans le fichier `.env` correspondant afin que les futures commandes la réutilisent.

---

<a id="5-create-your-first-joomla-site"></a>
## 5. Créez votre premier site Joomla

OctoJoom crée tout ce dont vous avez besoin : les réseaux Docker, la configuration Traefik, les fichiers d'environnement et le conteneur Joomla. Commencez par la tâche `setup` :

```bash
# Basic interactive setup
octojoom --type joomla --task setup
```

Lors de la configuration, fournissez le domaine, le sous-domaine, la clé et la version de Joomla. OctoJoom enregistre ces détails dans des fichiers `.env` dans son répertoire de projet.

Vous pouvez également fournir les valeurs dans une seule commande pour éviter les invites :

```bash
octojoom --type joomla --task setup \
  --key "mysite" \
  --env-key "MYSITE" \
  --domain "example.local" \
  --sub-domain "jcb" \
  --joomla-version "5.1"
```

Que se passe-t-il ensuite :

1. Les fichiers Docker Compose sont générés pour Traefik et votre conteneur Joomla.
2. OctoJoom s'assure que le proxy Traefik est en cours d'exécution.
3. Un conteneur Joomla est créé avec des montages de liaison pour un stockage persistant.
4. Les fichiers `.env` sont écrits (ou mis à jour) avec les paramètres que vous avez fournis.

Une fois la commande terminée, ouvrez votre navigateur sur le domaine choisi (par exemple, `http://jcb.example.local`). Terminez le programme d'installation Web de Joomla si vous y êtes invité, puis connectez-vous à l'interface administrateur.

---

<a id="6-manage-multiple-sites"></a>
## 6. Gérer plusieurs sites

Chaque site que vous créez possède son propre répertoire sous l'espace de travail OctoJoom. Traefik gère le routage, afin que chaque domaine puisse être actif simultanément sans conflit sur les ports. Les commandes utiles incluent :

* **Activer un site**```bash
  octojoom --type joomla --task enable --container "jcb.example.local"
  ```* **Désactiver un site**```bash
  octojoom --type joomla --task disable --container "jcb.example.local"
  ```* **Reconfigurer un site** – réexécutez `--task setup` pour ajuster les noms de domaine ou modifier les versions de Joomla. OctoJoom réutilise les volumes de données existants sauf si vous les supprimez explicitement.

Pour vérifier quels conteneurs sont en cours d'exécution, utilisez les commandes Docker telles que `docker ps` ou lisez la sortie d'état d'OctoJoom après chaque tâche.

---

<a id="7-environment-files-and-customisation"></a>
## 7. Fichiers d'environnement et personnalisation

OctoJoom gère plusieurs fichiers `.env` (par exemple, un pour Traefik et un par site). Le script vous indique où se trouve chaque fichier lorsqu'il met à jour une valeur. Vous pouvez les ouvrir dans votre éditeur pour modifier les paramètres avancés tels que :

* Étiquettes ou middlewares Traefik supplémentaires.
* Valeurs personnalisées de l'e-mail/mot de passe de l'administrateur Joomla.
* Volumes Docker supplémentaires pour les outils de développement.

Étant donné que ces fichiers alimentent Docker Compose, toutes les modifications prendront effet la prochaine fois que vous activerez le site.

---

<a id="8-install-joomla-component-builder-jcb"></a>
## 8. Installez Joomla Component Builder (JCB)

Une fois le conteneur Joomla en ligne :

1. Visitez la zone administrateur (par exemple, `http://jcb.example.local/administrator`).
2. Accédez à **Système → Installer → Extensions**.
3. Installez Joomla Component Builder à partir de votre package local ou du répertoire d'extensions Joomla.
4. Importez des packages de démonstration si nécessaire et poursuivez votre flux de travail JCB habituel.

Toutes les données Joomla se trouvent dans les volumes persistants du conteneur, vous pouvez donc reconstruire ou mettre à niveau le conteneur sans perdre votre travail.

---

<a id="9-updating-and-maintaining-your-stack"></a>
## 9. Mise à jour et maintenance de votre pile

* **Mettre à jour OctoJoom lui-même :** `octojoom --update --access-token <token>`
* **Tirez des images Joomla plus récentes :** réexécutez `octojoom --type joomla --task setup --joomla-version <tag>` et OctoJoom récupérera l'image spécifiée.
* **Supprimer un site :** désactivez-le d'abord, puis supprimez le répertoire du projet et les volumes Docker associés si vous n'avez plus besoin des données.
* **Fichiers journaux :** vérifiez les journaux du conteneur avec `docker compose logs` dans le répertoire du site lors du dépannage.

---

<a id="10-summary"></a>
## 10. Résumé

OctoJoom vous offre un flux de travail cohérent et conteneurisé pour le développement local de Joomla et JCB :

* Installez le script une fois.
* Utilisez `setup` pour lancer de nouveaux projets en quelques minutes.
* Gérez plusieurs sites simultanément sans conflits.
* Tirez parti de Traefik pour des noms de domaine soignés et mémorables.

En passant de Bitnami à OctoJoom, votre environnement local reste aligné sur les pratiques Docker modernes et les outils que nous utilisons en interne.