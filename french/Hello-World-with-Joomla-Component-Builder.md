> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="building-a-hello-world-component-with-joomla-component-builder"></a>
# Construire un composant "Hello World" avec Joomla Component Builder

*(Procédure complète pour débutant)*

<a id="tutorial-videohttpswwwyoutubecomwatchv1kbbtquxmtc"></a>
### [Vidéo didacticiel](https://www.youtube.com/watch?v=1KBBtQUxMTc)

---

<a id="introduction"></a>
## Introduction

[01:55](https://youtu.be/1KBBtQUxMTc?t=115)

Ce didacticiel vous apprend à créer un composant Joomla entièrement fonctionnel à partir de zéro à l'aide de **Joomla Component Builder (JCB)**.
Vous commencerez par la configuration la plus simple - un message d'accueil **"Hello World"** - et terminerez par une vue dynamique du site où vous pourrez lister, afficher et même modifier ces messages d'accueil depuis le frontend.

**Ce que vous ferez :**

1. Installez JCB
2. Créez un nouveau champ (`greeting`)
3. Créez une vue administrateur (`greetings`)
4. Créez et compilez un nouveau composant (`world`)
5. Ajouter des vues de site frontend
6. Lier les éléments de menu et ajouter des liens d'édition

Téléchargez ou explorez la dernière version de JCB à partir des [versions VDM GitHub](https://github.com/vdm-io/Joomla-Component-Builder), puis installez-la via **Extensions → Gérer → Installer**.

---

<a id="1-create-the-greeting-field"></a>
## 1. Créez le champ de voeux

[02:46](https://youtu.be/1KBBtQUxMTc?t=166)

Les champs définissent les colonnes de données que votre composant utilisera. Ici, vous allez créer un champ de texte simple qui stocke les salutations.

<a id="steps"></a>
### Étapes

1. Accédez à **JCB → Champs → Nouveau**.
2. Sous l'onglet **Définir les propriétés** :

* **Nom** → `greeting`
   * **Étiquette** → `Greeting`
   * **Tapez** → Sélectionnez **Texte**
3. Accédez à l'onglet **Base de données** :

* **Type de données** → `VARCHAR`
   * **Longueur** → `255`
   * **Commutateur nul** → `NOT NULL`
   * **Méthode de modélisation** → `Default`
4. Laissez les valeurs par défaut de **Catégorie** et **Publication** inchangées.
5. Cliquez sur **Enregistrer et fermer**.

> **Conseil :**
> L'onglet Base de données définit la colonne SQL que JCB va générer.
>
> * `VARCHAR(255)` stocke un texte court.
> * `NOT NULL` le rend obligatoire.
> * `Modelling Method` contrôle la gestion des données (JSON, base64, etc.) - "Par défaut" convient ici.

---

<a id="2-create-an-admin-view"></a>
## 2. Créer une vue administrateur

[03:51](https://youtu.be/1KBBtQUxMTc?t=263)

La **Vue Admin** connecte les champs à une table de base de données et crée les écrans de gestion backend de Joomla.

<a id="steps-1"></a>
### Étapes

1. Accédez à **Vues administrateur → Nouveau**.
2. Configurez les informations de base :

* **Nom (singulier)** → `greeting`
   * **Nom (pluriel)** → `greetings`
   * **Nom du système** → `greetings`
3. (Facultatif) Choisissez une icône.
4. Dans l'onglet **Champs**, cliquez sur **Ajouter un champ** et choisissez `greeting`.

* Marquez-le comme :

* **Afficher dans la liste**
     * **Première colonne**
     * **Champ Titre**
     * **Triable**
     * **Recherchable**
     * **Lié à la vue d'édition**
5. Cliquez sur **Enregistrer et fermer**.

Cette vue d'administration gère les enregistrements de messages d'accueil dans le backend.

---

<a id="3-create-the-component-world"></a>
## 3. Créez le composant "Monde"

[04:55](https://youtu.be/1KBBtQUxMTc?t=295)

Maintenant, vous reliez tout dans un véritable composant Joomla.

<a id="steps-2"></a>
### Étapes

1. Ouvrez **Composants → Nouveau**.
2. **Nom** → `World` (le nom du système se remplit automatiquement comme `world`).
3. (Facultatif) Sélectionnez une icône ou une image.
4. Sous **Paramètres de la vue administrateur** :

* Liez la vue d'administration principale à `Greetings`.
5. Activez les options suivantes (comme indiqué dans la vidéo) :

* Ajouter au menu principal
   * Autoriser le sous-menu
   * Vérification automatique
   * Histoire
   * Possède des métadonnées
   * A accès
   * Autoriser l'importation/exportation
6. Sous **Options d'affichage du site**, activez :

* **Créer une vue du site** → Oui
   * **Vue d'administration liée** → `Greetings`
   * **Possède une vue d'édition** → Oui
   * **Vue par défaut** → `Greetings`
7. **Enregistrer et fermer.**

---

<a id="4-compile-and-install-the-component"></a>
## 4. Compilez et installez le composant

[07:25](https://youtu.be/1KBBtQUxMTc?t=445)

1. Accédez au **Compilateur** dans JCB.
2. Sélectionnez votre nouveau composant (**Monde**).
3. Désélectionnez tous les éléments de construction facultatifs qui ne sont pas nécessaires.
4. Cliquez sur **Compiler**.

JCB génère tous les fichiers PHP, XML et SQL requis (≈ 8 000 lignes, 160 fichiers).
Une fois terminé, cliquez sur **Installer** pour l'ajouter directement à Joomla.

<a id="verify-the-admin-area"></a>
### Vérifiez la zone d'administration

* Accédez à **Composants → Hello World → Salutations**.
* Cliquez sur **Nouveau**, saisissez « Bonjour James Sable » et **Enregistrer et fermer**.
* Rouvrez, remplacez par "Bonjour Michael", enregistrez et vérifiez les **Versions**.
  [09:55](https://youtu.be/1KBBtQUxMTc?t=595)

Vous verrez le contrôle de version et les autorisations fonctionner automatiquement.

---

<a id="5-add-frontend-site-views"></a>
## 5. Ajouter des vues frontales (site)

[12:15](https://youtu.be/1KBBtQUxMTc?t=737)

JCB vous permet de créer rapidement des pages frontales (vues de site) pour afficher des données.

---

<a id="51-create-dynamic-gets"></a>
### 5.1 Créer des Gets dynamiques

[13:34](https://youtu.be/1KBBtQUxMTc?t=814)

**UN. Liste des articles**

1. **Obtentions dynamiques → Nouveau**
2. **Type** → Requête de liste
3. **Vue administrateur** → `Greetings`
4. **Pagination** → Non
5. Ajoutez un filtre WHERE :

   ```sql
   published = 1
   ```6. **Enregistrer et fermer**

**B. Article unique**

1. **Obtentions dynamiques → Nouveau**
2. **Tapez** → Obtenir l'article
3. **Vue administrateur** → `Greetings`
4. Filtre OÙ :

   ```sql
   id = {id}
   ```5. **Enregistrer et fermer**

---

<a id="52-create-site-views"></a>
### 5.2 Créer des vues de site

[17:05](https://youtu.be/1KBBtQUxMTc?t=1025)

**Vue en liste (`greetings`)**

```php
<ul>
<?php foreach ($this->items as $item): ?>
  <li><?php echo $item->greeting; ?></li>
<?php endforeach; ?>
</ul>
```

**Vue unique (`greet`)**

```php
<h2><?php echo $this->item->greeting; ?></h2>
```

> **Conseil :**
> Utilisez `greet` pour la vue unique afin d'éviter les conflits avec la vue d'édition `greeting`.

---

<a id="53-attach-site-views-to-component"></a>
### 5.3 Attacher des vues de site au composant

[20:30](https://youtu.be/1KBBtQUxMTc?t=1230)

1. Dans **Composant → Paramètres → Vues du site** :

* `greet` → pas de menu ; métadonnées sur
   * `greetings` → menu activé ; métadonnées sur ; définir par défaut
   * Accès → Public pour les deux
2. **Enregistrer et fermer**, puis **Compiler** et **Installer** à nouveau.

---

<a id="6-verify-frontend-and-public-access"></a>
## 6. Vérifiez le frontend et l'accès public

[24:00](https://youtu.be/1KBBtQUxMTc?t=1440)

Si vos nouvelles vues n'apparaissent pas publiquement :

1. Désinstallez le composant.
2. Réinstallez-le à nouveau - JCB applique l'accès public lors de la première installation.

Pour conserver les données existantes :

* Dans **Admin View → MySQL Tab**, activez la sauvegarde des tables.
* Exclure les champs volatils (`created_by`, `modified_by`, `access`, `asset_id`).
* Compilez avant de désinstaller.

---

<a id="7-link-a-menu-item"></a>
## 7. Lier un élément de menu

[27:40](https://youtu.be/1KBBtQUxMTc?t=1660)

1. Joomla → **Menus → Menu principal → Nouveau**
2. **Type d'élément de menu** → Composant → Hello World → `Greeting`
3. (Facultatif) Définir comme **Accueil**
4. **Enregistrez et fermez**, puis consultez le site.

Vous verrez "Bonjour Michael".

---

<a id="8-make-list-items-clickable-using-slug--route-helper"></a>
## 8. Rendre les éléments de la liste cliquables (à l'aide de Slug & Route Helper)

[31:10](https://youtu.be/1KBBtQUxMTc?t=1870)

```php
<ul>
<?php foreach ($this->items as $item): ?>
  <li>
    <a href="<?php echo JRoute::_('index.php?option=com_world&view=greet&id=' . $item->slug); ?>">
      <?php echo $item->greeting; ?>
    </a>
  </li>
<?php endforeach; ?>
</ul>
```

> **Remarque :**
> JCB crée automatiquement le `slug` dans le modèle (via `alias` + `id`).
> Vous pouvez également utiliser la méthode de route d'assistance :
> `WorldHelperRoute::getGreetRoute($slug)`

Recompiler et installer.

---

<a id="9-add-edit-links-on-frontend"></a>
## 9. Ajouter des liens de modification sur le frontend

[34:55](https://youtu.be/1KBBtQUxMTc?t=2095)

Dans l'**onglet PHP personnalisé** de la vue du site :

```php
$this->edit = JRoute::_('index.php?option=com_world&task=greeting.edit');
```

Dans le modèle :

```php
<a href="<?php echo $this->edit . '&id=' . $this->item->id; ?>">Edit</a>
```

Recompiler et installer.
Si vous cliquez sur **Modifier** sans autorisation, Joomla affiche « Non autorisé ».
Connectez-vous en tant qu'utilisateur autorisé pour voir le formulaire de modification.

---

<a id="10-verify-permissions-logic"></a>
## 10. Vérifier la logique des autorisations

[38:40](https://youtu.be/1KBBtQUxMTc?t=2320)

La classe d'assistance (`/admin/helpers/world.php`) contient :

```php
getActions($view, $id = 0)
```

Cela renvoie des autorisations telles que :

* `core.create`
* `core.edit`
* `core.delete`
* `core.edit.state`

Utilisez-les pour afficher ou masquer les boutons en fonction des droits des utilisateurs dans vos modèles.

---

<a id="result"></a>
## Résultat

Vous avez maintenant créé un composant Joomla qui prend en charge :

* Définitions des champs d'administration et intégration de la base de données
* Obtient dynamiques et vues du site
* Gestion des versions et autorisations
* Affichage et édition du frontend public

Votre nouveau composant **Hello World** démontre avec quelle rapidité JCB peut générer de puissantes applications Joomla en quelques clics seulement.

---
