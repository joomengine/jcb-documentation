> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-helper-structures-to-any-jcb-component"></a>
# Ajout de structures d'assistance à n'importe quel composant JCB

Ce guide vous guide tout au long du processus d'intégration des **structures d'aide**, telles que la documentation d'aide, dans n'importe quel composant Joomla Component Builder (JCB).
Il est basé sur le didacticiel vidéo officiel *"Ajout de structures d'assistance à n'importe quel composant JCB"* et développé pour plus de clarté, de précision et d'exhaustivité.

---

<a id="1-introduction-to-helper-structures"></a>
## 1. Introduction aux structures d'assistance

**[00:00:00](https://www.youtube.com/watch?v=nw9YPu9emws&t=0s)**

Une question s'est posée sur la manière d'intégrer un **Menu d'aide** dans les composants JCB. JCB comprend une zone **Document d'aide** qui permet aux développeurs de fournir de la documentation et une assistance contextuelle au sein de leurs composants.

Bien que le temps n'ait pas permis d'étendre en profondeur cette fonctionnalité dans la vidéo, le **système de documents d'aide** peut être facilement ajouté à n'importe quel composant JCB via une structure d'assistance.

---

<a id="2-obtaining-the-sermon-distributor-package"></a>
## 2. Obtention du package de distribution de sermons

**[00:00:39](https://www.youtube.com/watch?v=nw9YPu9emws&t=39s)**

Pour suivre cette démonstration, le **Sermon Distributor Package** est requis.
Ce package comprend des structures préconfigurées, telles que la **Vue d'administration du document d'aide**, qui peuvent être importées dans n'importe quel composant.

1. Visitez le référentiel VDM.io GitHub :
   `https://github.com/vdm-io/JCB-Packages`
2. Localisez le package **Sermon Distributor**.
3. Achetez la clé d'activation auprès de [http://vdm.bz/jcb-packages](http://vdm.bz/jcb-packages).

Une fois installé, toutes les données et instructions nécessaires sont incluses dans la documentation du package.

---

<a id="3-adding-the-help-document-admin-view"></a>
## 3. Ajout de la vue administrateur du document d'aide

**[00:02:48](https://www.youtube.com/watch?v=nw9YPu9emws&t=168s)**

1. Ouvrez votre composant de démonstration dans JCB.
   Par exemple : `com_demo`.
2. Accédez à **Vues d'administration** et cliquez sur **+** pour créer une nouvelle vue.
3. Nommez la vue **Document d'aide**.
4. Attribuez l'icône **Support**.
5. Configurez les options suivantes :

* **Métadonnées :** *Non requis*
   * **Accès :** *Non utilisé*
   * **Importer :** *Facultatif*
   * **Édition frontale :** *Désactivé*
   * **Position du menu :** *Deuxième position (facultatif)*

> **Conseil :** Si des problèmes de case à cocher apparaissent (les champs ne s'affichent pas correctement), fermez et rouvrez simplement le formulaire.
> JCB supprime progressivement les champs répétables au profit de **sous-formulaires**, qui offrent une meilleure flexibilité et une meilleure cohérence de la base de données.

Enregistrez et fermez la nouvelle vue administrateur.

---

<a id="4-compiling-and-installing-the-updated-component"></a>
## 4. Compilation et installation du composant mis à jour

**[00:04:52](https://www.youtube.com/watch?v=nw9YPu9emws&t=292s)**

1. Accédez à **Compilateur**.
2. Compilez votre composant de démonstration (`com_demo`).
3. Installez le fichier ZIP nouvellement compilé via le **Extension Manager** de Joomla.

> Assurez-vous que le composant n'est **pas déjà installé** avant de compiler ; sinon, des conflits de bases de données pourraient survenir.

Après l'installation, ouvrez le composant de démonstration et vérifiez qu'une nouvelle zone **Documents d'aide** a été ajoutée.

---

<a id="5-creating-a-new-help-document"></a>
## 5. Création d'un nouveau document d'aide

**[00:05:43](https://www.youtube.com/watch?v=nw9YPu9emws&t=343s)**

1. Accédez à **Documents d'aide** et cliquez sur **Nouveau**.
2. Définissez le **Groupe cible** sur *Tous*.
3. Sous **Emplacement**, sélectionnez une vue de la zone d'administration (par exemple, Tableau de bord ou Looks).
4. Fournissez un **Titre** et sélectionnez le **Type d'aide**.

<a id="help-types"></a>
### Types d'aide

<a id="a-external-url"></a>
#### un. URL externe

**[00:06:41](https://www.youtube.com/watch?v=nw9YPu9emws&t=401s)**
Utilisez-le lors de la distribution publique d'un composant.
Cela relie le contenu de l'aide à une **page externe** (telle qu'une documentation ou des didacticiels vidéo) qui peut être mise à jour sans avoir à envoyer une nouvelle version du composant.

<a id="b-text"></a>
#### b. Texte

**[00:07:20](https://www.youtube.com/watch?v=nw9YPu9emws&t=440s)**
Pour obtenir un contenu d'aide interne simple, choisissez **Texte** et saisissez directement les instructions.
Exemple:

> "C'est l'aide dont vous avez besoin."

Enregistrez et fermez l'enregistrement.

Une fois enregistrée, la vue ciblée (par exemple, **Looks**) affichera un nouveau bouton **Aide**, qui ouvre le contenu ou le lien dans un modal.

---

<a id="6-targeting-additional-views"></a>
## 6. Cibler des vues supplémentaires

**[00:08:32](https://www.youtube.com/watch?v=nw9YPu9emws&t=512s)**

Vous pouvez cibler soit :

* **Liste des vues** (au pluriel, par exemple, Looks)
* **Modifier les vues** (singulier, par exemple, Look)
* **Vues frontales** (zone du site)

Chacun peut avoir un contenu d’aide unique lié à différentes URL ou textes.

---

<a id="7-linking-help-documents-to-database-tables"></a>
## 7. Lier les documents d'aide aux tables de base de données

**[00:09:36](https://www.youtube.com/watch?v=nw9YPu9emws&t=576s)**

Pour envoyer votre composant avec un contenu d'aide intégré :

1. Accédez à **Vues administrateur → Document d'aide**.
2. Attribuez un **Nom du système**, par exemple `demo_help_document`.
3. Ajoutez un **Lien de table MySQL** :

* Activer *Lié à la table MySQL* : Oui
   * Choisissez la source : *Tableau*
   * Sélectionnez `demo_help_document`
   * Supprimez les champs inutiles (comme démontré dans la vidéo).

Enregistrez et fermez.

> **Important :** Compilez toujours le composant **avant de désinstaller** la version locale.

---

<a id="8-understanding-the-sql-insert-process"></a>
## 8. Comprendre le processus d'insertion SQL

**[00:11:57](https://www.youtube.com/watch?v=nw9YPu9emws&t=717s)**

Lorsque vous compilez le composant :

* Le fichier `install.mysql.utf8.sql` comprendra automatiquement :

* Code de création de table
  * Instruction `INSERT` pour les enregistrements du document d'aide par défaut

Cela signifie que les données d'aide (comme les liens et le texte) seront ajoutées à la base de données lors de l'installation du composant.

> Remarque : Ces inserts ne sont **pas inclus dans les fichiers de mise à jour**.
> Pour les mises à jour, utilisez **scripts personnalisés** dans l'onglet JCB PHP sous *Événements d'installation/mise à jour/désinstallation* pour réinsérer les données.

---

<a id="9-handling-missing-linked-tables"></a>
## 9. Gestion des tables liées manquantes

**[00:13:48](https://www.youtube.com/watch?v=nw9YPu9emws&t=828s)**

Si vous désinstallez le composant puis tentez de le recompiler, vous risquez de rencontrer l'erreur :

> `An error has occurred: Table 'demo.#_demo_help_document' doesn't exist`

Cela se produit car la table liée n'existe plus.
Pour résoudre ce problème :

1. Revenez à la **Vue Administrateur**.
2. Modifiez la source MySQL de **Table** à **Dump**.
3. Copiez le SQL de votre fichier de dump et collez-le dans le champ MySQL.

Vous pouvez désormais compiler le composant avec succès même s'il est désinstallé.

---

<a id="10-verifying-the-dump-file"></a>
## 10. Vérification du fichier de vidage

**[00:16:04](https://www.youtube.com/watch?v=nw9YPu9emws&t=964s)**

Après la recompilation, ouvrez le nouveau fichier ZIP et vérifiez le fichier `install.mysql.utf8.sql`.
Vous verrez que vos **Données de vidage** ont été correctement insérées, confirmant que les données du document d'aide sont désormais codées en dur dans le script d'installation.

---

<a id="11-about-the-sermon-distributor-helper-script"></a>
## 11. À propos du script d'aide du distributeur de sermons

**[00:16:45](https://www.youtube.com/watch?v=nw9YPu9emws&t=1005s)**

Vous pouvez créer votre propre structure de document d'aide à partir de zéro sans acheter le package Sermon Distributor.
Cependant, ce package inclut des **scripts PHP personnalisés** qui automatisent l'adaptation de la structure d'aide pour n'importe quel composant - une bonne référence pour les utilisateurs avancés.

---

<a id="12-how-jcb-detects-help-documents"></a>
## 12. Comment JCB détecte les documents d'aide

**[00:17:51](https://www.youtube.com/watch?v=nw9YPu9emws&t=1071s)**

Lorsque JCB détecte qu'une vue est un **document d'aide** et que les champs appropriés sont définis, il :

* Construit les comportements front-end et back-end
* Intègre les boutons d'aide contextuelle
* Prend en charge la liaison dynamique entre les vues de l'administrateur et du site

Cela permet aux utilisateurs de votre composant de modifier ou d'étendre le contenu de l'aide en fonction de leurs besoins.

---

<a id="13-summary"></a>
## 13. Résumé

**[00:18:59](https://www.youtube.com/watch?v=nw9YPu9emws&t=1139s)**

Vous avez maintenant appris à :

1. Ajoutez une **Vue d'administration du document d'aide** à n'importe quel composant.
2. Configurez et ciblez les entrées d'aide sur des vues spécifiques.
3. Liez les données d'aide à la base de données de votre composant.
4. Utilisez le mode **Dump** pour conserver les données pour la compilation.
5. Comprendre comment JCB détecte et intègre automatiquement les structures d'aide.

Ce processus rend vos composants plus **conviviaux** et **auto-documentés**, réduisant ainsi les demandes d'assistance et améliorant l'expérience utilisateur.

---
