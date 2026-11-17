> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="component-ftp-and-more"></a>
# Composant FTP et plus

(*Basé sur [Vidéo YouTube](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)*)
(*Cliquez sur les horodatages pour accéder à des sections spécifiques de la vidéo.*)

---

<a id="adding-readme-script"></a>
## Ajout du script README

[00:00:00](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h00m00s)

Le **script README** de Joomla Component Builder (JCB) vous permet d'ajouter une page d'introduction basée sur les démarques à votre composant. Ce fichier sert généralement de **page d'accueil ou de page de destination** de votre composant une fois que les utilisateurs y accèdent sur GitHub ou le gestionnaire d'extensions de Joomla.

Par exemple, lors de la visualisation d'un référentiel de composants sur GitHub, le fichier README affiche des informations telles qu'une image, une description et une mise en page. Ceux-ci sont tous définis au format Markdown et stockés dans le composant.

Pour afficher la version brute de ce fichier README, cliquez sur **"Raw"** dans GitHub - cela vous montre la syntaxe exacte de démarque.
Dans JCB, vous pouvez ajouter à la fois le **README** et le **TEXTE README** directement dans les paramètres de votre composant.

Ces sections utilisent des **espaces réservés** (par exemple : `###version###`) qui extraient automatiquement les informations dynamiques des métadonnées du composant.

---

<a id="placeholders"></a>
## Espaces réservés

[00:01:10](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h01m10s)

Le symbole `#` en démarque indique un **en-tête** (H1-H6). Il est essentiel de comprendre la syntaxe de base de Markdown lors de l'édition du script README.

Dans la zone de texte JCB README, les espaces réservés tels que `###version###`, `###author###` ou `###component_name###` sont automatiquement remplacés par leurs valeurs réelles lors de la compilation.

Si vous mettez à jour la version de votre composant, ces espaces réservés refléteront automatiquement la nouvelle version – aucune modification manuelle n'est nécessaire.

---

<a id="component-builder-link-back-info"></a>
## Informations de retour du lien vers le constructeur de composants

[00:01:59](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h01m59s)

La **section de liens** du README de JCB vous permet de fournir des **ressources utiles** ou des **liens communautaires**.
Ici, vous pouvez inclure :

* Liens vers des **menus d'aide** ou de la documentation
* Instructions d'installation
* Informations sur la communauté ou la contribution

Bien que cette section ne soit pas obligatoire, il est encouragé de laisser les informations de lien en place pour aider les autres à découvrir et à soutenir le projet JCB. Cela garantit que la communauté au sens large continue de croître et de rester connectée.

---

<a id="markdown-reference"></a>
## Référence de démarque

[00:02:46](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h02m46s)

Pour obtenir des conseils sur la syntaxe Markdown, reportez-vous à la documentation officielle :
[Aide-mémoire Markdown](https://www.markdownguide.org/cheat-sheet/)

---

<a id="admin-and-site-views---adding-or-editing"></a>
## Vues d'administration et de site – Ajout ou modification

[00:03:06](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h03m06s)

Dans les sections **Admin View** et **Site View** de JCB, vous pouvez :

* Créez de **nouvelles vues** pour votre composant.
* **Modifier les vues d'administrateur ou de site existantes**.

> **Important :**
> La création d'une nouvelle vue d'administration ici ne la lie **pas automatiquement** à votre composant.
> Pour le lier, accédez à la zone **Paramètres → Vues d'administration** du composant et sélectionnez les vues que vous souhaitez associer.

Cette interface fournit simplement un moyen rapide de gérer les vues d'administration et de site associées à partir de l'éditeur de composants.

---

<a id="ftp-info---updating-components"></a>
## Informations FTP - Mise à jour des composants

[00:03:57](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h03m57s)

Les **Paramètres du serveur FTP** permettent le déploiement automatique de votre composant compilé sur votre serveur distant et la configuration du **Support du serveur de mise à jour Joomla**.

<a id="joomla-update-server-integration"></a>
### Intégration du serveur de mise à jour Joomla

Joomla utilise un **serveur de mise à jour** pour informer les utilisateurs lorsque de nouvelles versions sont disponibles.
Dans JCB, si vous définissez **Update Server** sur **Oui**, le compilateur inclura automatiquement ces informations dans le fichier manifeste XML du composant.

S'il est défini sur **Non**, le serveur de mise à jour sera omis.

<a id="ftp-configuration"></a>
### Configuration FTP

Pour activer les importations automatiques, configurez les champs suivants dans les **paramètres FTP** de votre composant :

* **Hôte FTP :** Le domaine ou l'adresse IP de votre serveur.
* **Port :** Le port FTP par défaut est `21`.
* **Nom d'utilisateur / Mot de passe :** Informations d'identification avec accès en écriture au dossier cible de votre composant.
* **Type binaire :** Généralement `15` ou `21` (JCB par défaut).

Lors de la compilation, JCB se connecte à votre serveur FTP, télécharge le composant ZIP compilé dans le dossier spécifié, puis se déconnecte automatiquement.

---

<a id="ftp-info---sales-server"></a>
## Informations FTP - Serveur de vente

[00:06:32](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h06m32s)

Le **Sales Server** fonctionne de manière similaire au serveur de mise à jour, mais a un objectif différent :

* **Serveur de mise à jour :** Informe les utilisateurs des mises à jour disponibles.
* **Sales Server :** héberge et donne accès au **package ZIP de composants** pour la vente ou la distribution.

Vous pouvez l'héberger sur votre propre serveur Web ou via un service tel que **WHMCS**.
Créez un compte FTP pointant directement vers le dossier qui stocke vos ZIP distribuables.

Lors de la compilation, si **"Ajouter un dossier de sauvegarde"** et **"Enregistrer le serveur de vente"** sont tous deux définis sur **Oui**, JCB :

* Déplacez le fichier ZIP compilé vers le dossier Sales Server.
* Créez une copie de sauvegarde localement.

---

<a id="global-options-and-encryption"></a>
## Options globales et cryptage

[00:07:49](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h07m49s)

Les options globales définissent les chemins de clé et les paramètres de chiffrement pour JCB.
Vous pouvez y accéder dans **Joomla → Composants → Component Builder → Options**.

<a id="encryption"></a>
### Cryptage

Certains champs, comme les informations d'identification FTP, sont **chiffrés** pour des raisons de sécurité.
Vous verrez un champ de clé de cryptage dans les paramètres globaux.

* Lorsque vous ajoutez votre propre clé de cryptage, JCB crypte les données stockées (comme les détails FTP).
* Changer cette clé ultérieurement rendra **impossible le déchiffrement** des données existantes.

En cas de modification, toutes les informations cryptées (telles que les informations d'identification FTP) doivent être ressaisies.

> **Remarque :** JCB prend en charge deux types de cryptage :
>
> * **Cryptage de base (clé de base)** - par défaut et suffisant pour FTP et les informations d'identification.
> * **Cryptage avancé** - pour des besoins de protection des données plus complexes.

---

<a id="folder-paths-and-git-integration"></a>
## Chemins de dossiers et intégration Git

[00:09:13](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h09m13s)

<a id="compiler-and-custom-folders"></a>
### Compilateur et dossiers personnalisés

* Ces chemins dépendent du système et ne sont pas flexibles.
* Il est préférable de **laisser ces champs vides**, sauf si cela est absolument nécessaire.

<a id="backup-and-git-folders"></a>
### Sauvegarde et dossiers Git

* **Dossier de sauvegarde :** Utilisé pour les sauvegardes de composants locaux.
* **Dossier Git :** Utilisé pour les référentiels de contrôle de version.

Lors de la compilation, JCB :

1. Générez tous les fichiers de composants dans le **dossier Git** (non compressés).
2. Remplacez les anciens fichiers par des fichiers mis à jour (Git suivra les modifications apportées aux fichiers).
3. Laissez votre référentiel Git intact : seuls les fichiers modifiés sont mis à jour.

Vous pouvez ensuite transférer le dossier vers **GitHub**, **GitLab** ou n'importe quel serveur Git.

> **Conseil :** Si vous débutez avec Git, explorez les cours pour débutants sur [Lynda.com](https://www.google.com/search?q=lynda.com+courses) ou Udemy.

---

<a id="ftp-folder-access-rules"></a>
## Règles d'accès aux dossiers FTP

[00:11:18](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h11m18s)

Assurez-vous que le compte FTP utilisé se connecte **directement** au dossier dans lequel JCB doit télécharger les ZIP des composants.
Les sous-dossiers ne sont **pas pris en charge**.

Lors de la compilation, le processus FTP de JCB se connecte, place le fichier et se déconnecte.
Ces identifiants FTP correspondent au chemin du dossier accessible depuis votre installation Joomla.

---

<a id="compilerphp---ftp-functions"></a>
## Compiler.PHP - Fonctions FTP

[00:12:32](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h12m32s)

Dans le backend, le fichier compilateur de JCB (`compiler.php`) inclut des fonctions spécifiques pour la gestion des transferts FTP.

<a id="key-functions"></a>
### Fonctions clés

* **`moveFileToFTPServer()`** - Transfère le ZIP compilé vers la destination FTP configurée.
* **`getFTP()`** - Vérifie les connexions FTP existantes et charge les informations d'identification pertinentes.

Ces fonctions utilisent la **Bibliothèque client FTP (`/libraries/joomla/client/ftp.php`)** de Joomla.
Ils gèrent en toute sécurité l'hôte, le port, le nom d'utilisateur et le mot de passe pendant la transmission des fichiers, garantissant ainsi qu'aucune donnée sensible n'est exposée.

---

<a id="update-server---versioning-and-sql-updates"></a>
## Update Server - Gestion des versions et mises à jour SQL

[00:14:23](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h14m23s)

Le **fichier XML du serveur de mise à jour** définit toutes les versions publiées et leurs liens de téléchargement correspondants.

<a id="version-management"></a>
### Gestion des versions

Lorsque vous publiez des mises à jour, pensez à :

* Quels **nouvelles vues ou champs** ont été ajoutés.
* Si des **modifications de la structure de la base de données** sont nécessaires.

Si votre nouvelle version modifie la base de données, vous pouvez utiliser la fonctionnalité **Mises à jour de version** de JCB pour attacher un **script SQL** à cette version.

Exemple:

* La version **1.2.9** nécessite une modification du tableau.
* Ajoutez votre commande SQL (en utilisant les conventions Joomla telles que `#__table_name`).
* JCB l'exécutera pendant le processus de mise à jour.

Chaque version doit avoir :

* Le **dump SQL de mise à jour** (si nécessaire).
* Le **lien de téléchargement** pour le ZIP mis à jour.
* Numéros de version qui **s'incrémentent logiquement**.

> **Exemple :**
>
> * `1.2.9` → `1.3.0` → `1.3.1` → `1.3.2`
> La dernière version de la liste doit correspondre à la version actuelle définie dans le composant.

Vous pouvez héberger des mises à jour sur n'importe quelle plateforme : **GitHub**, **Bitbucket** ou votre URL personnalisée.

---

<a id="conclusion"></a>
## Conclusion

[00:18:26](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h18m26s)

Ceci conclut la présentation de **Component FTP et plus** dans Joomla Component Builder.
Nous avons expliqué comment :

* Ajouter et gérer le script de démarque README
* Configurer les vues d'administration et de site
* Configurer FTP pour le déploiement et les mises à jour
* Utiliser les serveurs de vente et de mise à jour
* Gérer les options globales et le cryptage
* Configurer les chemins de dossiers et l'intégration de Git
* Comprendre la gestion des versions et des mises à jour SQL

Une fois que vous avez configuré votre composant, vous êtes prêt à procéder à la **création des vues frontales du site**.
N'oubliez pas : commencez toujours par les vues d'administration, puis passez aux vues de site pour une structure complète des composants Joomla.

[00:19:06](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h19m06s)

---
