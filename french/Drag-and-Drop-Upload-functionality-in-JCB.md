> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="drag-and-drop-upload-functionality-in-joomla-component-builder-jcb"></a>
# **Fonctionnalité de téléchargement par glisser-déposer dans Joomla Component Builder (JCB)**

<a id="overview"></a>
## **Aperçu**

**Source vidéo :** [Tutoriels VDM - Fonctionnalité de téléchargement par glisser-déposer dans JCB](https://www.youtube.com/watch?v=UvzDyVQyHDI)
Ce guide explique comment créer un téléchargeur de fichiers dynamique par glisser-déposer au sein de la structure des composants de JCB, y compris la gestion Ajax côté serveur, le recadrage automatisé des images et le stockage sécurisé des fichiers.

---

<a id="1-introduction-to-the-drag-and-drop-functionality"></a>
## **1. Introduction à la fonctionnalité Glisser-Déposer**

**[00:00:00](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h00m00s)**
Ce didacticiel présente la **fonctionnalité de recadrage automatisé par glisser-déposer**, qui complète le **Type de champ de fichier** standard de JCB.

Bien que le champ Fichier soit plus simple, cette méthode ajoute :

* Téléchargement dynamique avec Ajax
* Recadrage d'images
* Meilleure UX grâce aux composants UIkit

---

<a id="2-setting-up-the-front-end-upload-with-uikit"></a>
## **2. Configuration du téléchargement frontal avec UIkit**

**[00:01:13](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h01m13s)**

<a id="step-1-choose-a-ui-library"></a>
### **Étape 1 : Choisissez une bibliothèque d'interface utilisateur**

JCB prend en charge plusieurs bibliothèques frontales.
Pour ce didacticiel, **UIkit v2** est utilisé (bien que vous puissiez le remplacer par Bootstrap ou UIkit v3).

> **Conseil :**
> Accédez à **UIkit v2 → Composants → Télécharger** pour consulter la documentation officielle de téléchargement.

---

<a id="3-adding-html-and-javascript-for-drag-and-drop"></a>
## **3. Ajout de HTML et JavaScript pour le glisser-déposer**

**[00:03:20](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h03m20s)**

Le HTML définit la zone de dépôt et les messages d'état ; le JavaScript gère la progression du téléchargement et les appels Ajax.

Vous pouvez ajouter ce balisage et ce script dans une **Note de code personnalisée** dans votre vue d'administration JCB.

Exemple de structure :

```html
<div id="upload-drop-main-documents" class="uk-placeholder">
  <p>Drop files here or <a class="uk-form-file">select one</a></p>
  <div id="progressbar-main-documents" class="uk-progress uk-hidden">
    <div class="uk-progress-bar" style="width: 0%;"></div>
  </div>
</div>
```

> **Options dynamiques :**
>
> * L'**URL de téléchargement** change dynamiquement en fonction du mode de fichier unique/multiple.
> * Les types de fichiers acceptés sont transmis à partir des paramètres du composant.
> * Ajax permet le téléchargement de fichiers avant de sauvegarder l'enregistrement principal.

---

<a id="4-handling-unsaved-items"></a>
## **4. Gestion des éléments non enregistrés**

**[00:05:40](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h05m40s)**

Lorsqu'un fichier est téléchargé mais que l'élément n'a **pas encore d'ID**, JCB stocke le nom du fichier téléchargé dans un **champ de formulaire caché**.
Une fois l'élément enregistré, les données du fichier sont automatiquement liées à cet enregistrement.

---

<a id="5-importing-the-required-jcb-packages"></a>
## **5. Importation des packages JCB requis**

**[00:06:21](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h06m21s)**

Avant de créer le programme de mise en ligne, importez les **packages VDM** qui incluent le composant **Document Manager** :

1. Accédez à **Composants Joomla → Importer des composants**.
2. Sélectionnez l'onglet **Packages VDM**.
3. Récupérer depuis GitHub → Vérifier la somme de contrôle → Importer.

> Le système confirme "**Validation de la somme de contrôle du package PASSÉ !**"

---

<a id="6-setting-allowed-file-formats"></a>
## **6. Définition des formats de fichiers autorisés**

**[00:12:03](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h12m03s)**

Accédez à votre **Composant → Options → Onglet Média**, puis définissez :

* **Formats de documents autorisés** (par exemple, PDF)
* **Formats multimédias autorisés** (par exemple, MP3)
* **Formats d'image autorisés** (par exemple, JPEG)

Définissez les **dimensions de recadrage** souhaitées (par exemple, largeur=200, hauteur=350) pour le redimensionnement de l'image.

---

<a id="7-demonstrating-the-upload-in-action"></a>
## **7. Démonstration du téléchargement en action**

**[00:13:11](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h13m11s)**

L'interface affiche désormais les zones de téléchargement dynamique :

* "Téléchargez votre image"
* "Téléchargez vos documents"
* "Téléchargez vos médias"

Les formats et dimensions autorisés sont affichés automatiquement, issus de la configuration globale.

> Tous les téléchargeurs (images, documents, médias) sont gérés via des extraits JavaScript réutilisables.

---

<a id="8-understanding-the-javascript-snippets"></a>
## **8. Comprendre les extraits JavaScript**

**[00:22:01](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h22m01s)**

L'extrait principal est `uikitFileUploader`, qui :

* Obtient dynamiquement les formats autorisés.
* Utilise `JRouter` pour acheminer correctement les appels Ajax pour les vues Administrateur et Site.
* Met à jour le DOM avec des barres de progression et des types de fichiers autorisés.

Chaque téléchargeur (document, image, média) utilise le même script, en modifiant uniquement les arguments transmis.

---

<a id="9-security-and-encryption-layers"></a>
## **9. Couches de sécurité et de chiffrement**

**[00:30:21](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h30m21s)**

Pour protéger les téléchargements :

* Utilisez **Medium Encryption (local-file-key)** pour un stockage plus sûr.
* Les fichiers derrière le dossier `/public_html` ne sont pas accessibles directement.
* Seuls les utilisateurs autorisés peuvent télécharger ou supprimer des téléchargements.

---

<a id="10-server-side-ajax-implementation"></a>
## **10. Implémentation Ajax côté serveur**

**[00:51:28](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h51m28s)**

Dans la **Vue Administrateur (Documents)** du composant, ajoutez une **Zone de code personnalisée** nommée `phpAjaxUploader`.

La logique PHP :

1. Valide les vues et formats autorisés.
2. Déplace les fichiers téléchargés vers les dossiers appropriés.
3. Génère des noms de fichiers sécurisés et aléatoires.
4. Redimensionne éventuellement les images à l'aide d'une classe d'assistance (`resizeImage`).
5. Crypte les métadonnées du fichier avant de l'enregistrer.

---

<a id="11-creating-component-configuration-fields"></a>
## **11. Création de champs de configuration de composant**

**[00:54:48](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h54m48s)**

Pour ajouter des formats de téléchargement configurables :

1. Accédez à **Paramètres → Créer une configuration de composant**.
2. Ajoutez des **Champs de liste** pour les formats de document, d'image et de média.
3. Activez « Autoriser la sélection multiple ».

Ces valeurs de configuration sont ensuite récupérées dynamiquement par les scripts de téléchargement.

---

<a id="12-functions-breakdown"></a>
## **12. Répartition des fonctions**

<a id="uploadfile"></a>
### **télécharger le fichier**

**[00:57:45](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h57m45s)**

* Valide la vue de téléchargement et le type de fichier.
* Utilise `getPackageFromUpload()` pour traiter les fichiers téléchargés.
* Renvoie la réponse Ajax avec le nom de fichier et l'état de réussite.

<a id="uploadnow"></a>
### **télécharger maintenant**

Gère le déplacement des fichiers et des déclencheurs :

* Redimensionnement de l'image (le cas échéant).
* Cryptage des fichiers documents/médias.
* Mises à jour de la base de données via Ajax.

<a id="setfilenamearray"></a>
### **setFileNameArray**

**[01:10:47](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=01h10m47s)**
Utilisé pour gérer plusieurs téléchargements lorsque l'élément existe déjà (possède un ID).

<a id="removefile"></a>
### **supprimer le fichier**

**[01:12:53](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=01h12m53s)**
Valide les autorisations des utilisateurs et supprime les fichiers du serveur et de la base de données.

---

<a id="13-demonstrations"></a>
## **13. Démonstrations**

<a id="uploading-an-image"></a>
### **Téléchargement d'une image**

**[00:43:18](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h43m18s)**
Faites glisser une image dans la zone de dépôt : elle est téléchargée, recadrée et affichée instantanément.

<a id="uploading-a-document"></a>
### **Téléchargement d'un document**

**[00:44:51](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h44m51s)**
Glissez et déposez des PDF ; des liens sont générés pour le téléchargement.

<a id="uploading-media-files"></a>
### **Téléchargement de fichiers multimédia**

**[00:48:17](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h48m17s)**
Téléchargez plusieurs fichiers MP3 simultanément ; Ajax les enregistre directement dans la base de données.

---

<a id="14-download-and-controller-integration"></a>
## **14. Téléchargement et intégration du contrôleur**

**[00:46:57](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h46m57s)**
Une **tâche de contrôleur** personnalisée (`download`) gère les téléchargements de fichiers sécurisés à l'aide d'URL chiffrées.

---

<a id="15-summary"></a>
## **15. Résumé**

**[01:16:52](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=01h16m52s)**

Ce système avancé de téléchargement par glisser-déposer fournit :

* Téléchargements Ajax en temps réel
* Recadrage et redimensionnement automatisés
* Gestion des fichiers sécurisée et cryptée
* Interaction conviviale
* Réutilisation modulaire via des extraits personnalisés

> **Remarque :** Il s'agit d'une implémentation avancée nécessitant de solides connaissances de l'architecture **JavaScript, PHP et JCB**. Le débogage et l'adaptation de votre composant sont nécessaires.

---

<a id="16-key-advantages"></a>
## **16. Avantages clés**

* Les utilisateurs n'interfèrent jamais avec les téléchargements des autres.
* UX améliorée par rapport au Media Manager natif de Joomla.
* Contrôle total sur les formats, le recadrage et les chemins de stockage.

---

<a id="17-helpful-links"></a>
## **17. Liens utiles**

* **Documentation de téléchargement UIkit :** [https://getuikit.com/v2/docs/upload.html](https://getuikit.com/v2/docs/upload.html)
* **Extraits VDM GitHub :** [https://github.com/vdm-io](https://github.com/vdm-io)
* **Générateur de composants Joomla :** [https://joomlacomponentbuilder.com](https://joomlacomponentbuilder.com)

---
