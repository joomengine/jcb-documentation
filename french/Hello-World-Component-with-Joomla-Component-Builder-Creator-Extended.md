> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="building-a-hello-world-component-with-joomla-component-builder-v260"></a>
# Construire un composant Hello World avec Joomla Component Builder v2.6.0

*Basé sur le didacticiel : "Hello World Component with Joomla Component Builder Creator - Extended"* 
*(Mise à jour pour JCB v2.6.0)*

---

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s) 
Ce guide explique comment créer un **Hello World Component** à l'aide de **Joomla Component Builder (JCB)** version **2.6.0**. 
JCB est un framework complet permettant de créer visuellement des composants Joomla, d'automatiser le code répétitif et de maintenir des conventions uniformes entre les projets.

---

<a id="1-introduction-to-joomla-component-builder"></a>
## 1. Introduction au générateur de composants Joomla

<a id="purpose"></a>
### But

[00:00:41](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m41s) 
JCB automatise la création de composants Joomla en compilant des structures passe-partout standardisées dans des extensions installables. 
Les modifications apportées dans le compilateur JCB sont instantanément appliquées à tous les composants.

<a id="key-concept"></a>
### Concept clé

- Effectuez **une modification**, recompilez-la et appliquez-la à tous les composants.
- Maintenir des **conventions orientées objet** cohérentes.
- JCB gère automatiquement la génération de code passe-partout pour les composants Joomla.

---

<a id="2-requirements-and-setup"></a>
## 2. Exigences et configuration

<a id="prerequisites"></a>
### Prérequis

[00:04:08](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s) 
- Connaissance de base de **PHP** et de l'**API Joomla**. 
- Familiarité avec les **structures de bases de données** (tables, champs et relations).

> **Conseil :** Si vous êtes nouveau dans le développement Joomla, consultez les *structures XML du gestionnaire d'articles* de Joomla pour des exemples de mappages de champs de base de données.

<a id="recommended-environment"></a>
### Environnement recommandé

[00:08:01](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m01s) 
- Installez Joomla localement ou sur un serveur de développement privé.
- Utilisez un IDE (tel que PhpStorm ou VS Code) pour éditer le code généré par JCB.

> Une configuration locale facilite l'extraction du code personnalisé et sa réimportation lors de la compilation.

---

<a id="3-installing-joomla-component-builder"></a>
## 3. Installation du générateur de composants Joomla

<a id="step-1-access-joomla-admin"></a>
### Étape 1 : Accédez à l'administrateur Joomla

[00:09:56](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m56s) 
Accédez à **Système → Gérer → Installer**.

<a id="step-2-choose-installation-method"></a>
### Étape 2 : Choisissez la méthode d'installation

- **Depuis le package :** Téléchargez le `.zip` de JCB depuis GitHub ou le site officiel. 
- **Depuis l'URL :** Collez l'URL du référentiel GitHub. 
- **À partir du Web :** Recherchez « Component Builder » sous *Outils → Outils de développement* et cliquez sur **Installer**.

> Le package JCB est volumineux ; la vitesse d'installation dépend de votre connexion Internet.

---

<a id="4-understanding-jcbs-structure"></a>
## 4. Comprendre la structure de JCB

<a id="components-admin-views-and-fields"></a>
### Composants, vues d'administration et champs

[00:11:57](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m57s) 
Pour créer un composant :
1. Définissez les **Types de champs**.
2. Créez des **Champs** à l'aide de ces types de champs.
3. Créez des **Vues d'administration**, qui font office de tables de base de données.
4. Liez les vues d'administration à votre **composant**.

**Relations :**
- **Vues administrateur** → Tables de base de données 
- **Champs** → Colonnes de base de données 
- **Types de champs** → Définitions de champs XML

<a id="backend-before-frontend"></a>
### Backend avant le frontend

[00:13:34](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m34s) 
Créez toujours le backend (vues d'administration et structure de la base de données) avant de créer des vues de site frontales.

---

<a id="5-creating-field-types"></a>
## 5. Création de types de champs

[00:14:15](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m15s) 
JCB est préchargé avec de nombreux **Types de champs** (par exemple, Texte, Radio, Case à cocher, Date, Liste). 
Vous pouvez les étendre ou les modifier au fur et à mesure de l'évolution de Joomla.

> **Remarque :** Joomla est obsolète *Champs répétables* ; utilisez plutôt **Champs de sous-formulaire**.

<a id="example-adding-a-custom-field-type"></a>
### Exemple : Ajout d'un type de champ personnalisé

1. Accédez à **Types de champs → Nouveau**.
2. Définissez ses **propriétés** :
   - Nom 
   - Valeur par défaut 
   - Ajustable / Obligatoire / Traduisible 
   - Descriptif

Exemple de définition XML dans un type de champ :

```xml
<field
    name="example_text"
    type="text"
    label="Example Text"
    description="Add your text here."
    required="true"
    default=""
/>
```

---

<a id="6-creating-fields"></a>
## 6. Création de champs

[00:17:42](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m42s)
Nous allons créer un **Champ de texte** nommé "Salutations".

<a id="steps"></a>
### Étapes

1. Accédez à **Champs → Nouveau**.
2. Sélectionnez **Type de champ : Texte**.
3. Remplissez les détails :

* **Étiquette :** `Greetings`
   * **Nom :** `greeting`
   * **Indice :** `Add greeting here`
   * **Tapez :** Texte
   * **Par défaut :** (laisser vide)
4. Enregistrez et fermez.

---

<a id="7-creating-an-admin-view"></a>
## 7. Création d'une vue administrateur

[00:24:46](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m46s)
Les vues d'administration représentent vos tables de base de données back-end.

<a id="step-by-step"></a>
### Étape par étape

1. Accédez à **Vues administrateur → Nouveau**.
2. **Nom du système :** `greetings_first`
3. **Vue d'un seul enregistrement :** `Greeting`
4. **Vue des enregistrements de liste :** `Greetings`
5. **Type :** `Read & Write`
6. **Brève description :** `Manages greetings records`
7. Enregistrez la vue une fois (cela crée la structure de la base de données).

<a id="linking-fields"></a>
### Liaison des champs

[00:29:45](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m45s)

1. Ouvrez l'onglet **Champs et conditions**.
2. Cliquez sur **Créer des champs liés** → Ajouter les champs que vous avez créés.
3. Configurez les propriétés du champ :

* Afficher dans la vue Liste des administrateurs.
   * Ordre (par exemple, "Nom" en premier, "Salutations" en second).
   * Définissez les éléments triables, consultables et pouvant être liés selon les besoins.

Exemple de configuration :

```json
{
  "field": "greetings",
  "list_order": 2,
  "sortable": true,
  "searchable": true,
  "linkable": false
}
```

Enregistrez et fermez la vue administrateur.

---

<a id="8-creating-the-component"></a>
## 8. Création du composant

[00:33:11](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h33m11s)
Créez maintenant le **composant Hello World**.

<a id="steps-1"></a>
### Étapes

1. Accédez à **Composants → Nouveau**.
2. **Nom du système :** `hello_world_v2`
3. **Nom du code :** `Hello World`
4. **Version :** `2.0.0`
5. Ajoutez le nom de l'entreprise, l'auteur et la description.
6. Enregistrez une fois.

<a id="link-the-admin-view"></a>
### Lier la vue administrateur

[00:34:01](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h34m01s)
Dans les paramètres du composant :

* Cliquez sur **Créer une vue d'administration de composant**.
* Sélectionnez la vue **Salutations** créée précédemment.
* Choisissez une icône (Icomoon par défaut) et attribuez-la au menu principal.
* Activez « Ajouter un enregistrement » sur le tableau de bord.

Activez les éléments suivants :

* Enregistrement automatique
* Conserver l'historique
* Possède des métadonnées
* Contrôle d'accès (public / enregistré / spécial)

Enregistrez et fermez.

---

<a id="9-compiling-and-installing-the-component"></a>
## 9. Compilation et installation du composant

[00:43:04](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h43m04s)

1. Accédez à **Compilateur**.
2. Sélectionnez votre composant.
3. Cliquez sur **Compiler**.

JCB générera :

* ~9 000 lignes de PHP
* 51 dossiers
* 122 fichiers

[00:44:17](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h44m17s)
Une fois compilé, cliquez sur **Installer sur ce site Joomla** ou utilisez le package `.zip` via le programme d'installation de Joomla.

---

<a id="10-adding-icons-and-images"></a>
## 10. Ajout d'icônes et d'images

[00:44:42](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h44m42s)
Si votre composant n'a pas d'icône :

1. Modifiez la vue administrateur → attribuez des icônes pour « Liste » et « Ajouter ».
2. Recompilez et réinstallez.

Vous verrez maintenant les nouvelles icônes dans l'administrateur Joomla.

---

<a id="11-adding-dynamic-gets"></a>
## 11. Ajout de GET dynamiques

[00:48:42](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h48m42s)
Les GET dynamiques sont des requêtes qui définissent les données qui sont extraites de la base de données de votre composant pour une utilisation frontale.

<a id="create-two-dynamic-gets"></a>
### Créer deux GET dynamiques

* **ListGreetings :** renvoie tous les messages d'accueil publiés.
* **Message d'accueil :** renvoie un message d'accueil par ID.

Exemple de configuration pour **ListGreetings** :

```php
WHERE a.published = 1
ORDER BY a.ordering ASC
```

Pour **Message d'accueil**, ajoutez :

```php
WHERE a.id = :id
```

et transmettez l'ID via l'URL.

Vous pouvez également rejoindre la table des utilisateurs de Joomla :

```sql
JOIN #__users AS b ON a.created_by = b.id
```

Enregistrez les deux GET dynamiques.

---

<a id="12-creating-site-views"></a>
## 12. Création de vues de site

<a id="site-view-1-list-view-greetings"></a>
### Vue du site 1 : vue en liste ("Salutations")

[00:58:30](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h58m30s)

1. Accédez à **Vues du site → Nouveau**.
2. **Nom du système :** `greetings`
3. **Nom du code :** `greetings`
4. **Obtenir principal :** `ListGreetings`
5. Enregistrez.

<a id="snippet-example"></a>
#### Exemple d'extrait de code

```php
<?php foreach ($this->items as $item) : ?>
    <p><?php echo $item->name; ?></p>
<?php endforeach; ?>
```

---

<a id="site-view-2-single-view-greeted"></a>
### Vue du site 2 : vue unique (« Accueilli »)

[01:23:56](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h23m56s)

1. Créez une autre vue de site appelée **Salut**.
2. **Obtenir principal :** `Greeting`
3. Ajoutez un panneau d’affichage simple.

Exemple:

```php
<div class="uk-panel">
  <h3><?php echo $this->item->name; ?></h3>
  <p><?php echo $this->item->greeting; ?></p>
</div>
```

Liez les deux vues du site au composant sous **Composant → Vues du site**.

---

<a id="13-adding-the-component-to-the-frontend-menu"></a>
## 13. Ajout du composant au menu frontend

[01:09:53](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h09m53s)

1. Créez plusieurs salutations dans le backend.
2. Accédez à **Menus → Menu principal → Nouvel élément de menu**.
3. Choisissez **Type de menu : Hello World → Salutations (site)**.
4. Enregistrez et fermez.

Si « La page ne redirige pas correctement » se produit, vérifiez le **Contrôle d'accès** sur la vue du site :

* Assurez-vous que `Public` est sélectionné.

---

<a id="14-adding-the-alias-field-for-seo-friendly-urls"></a>
## 14. Ajout du champ Alias ​​pour les URL optimisées pour le référencement

[01:14:11](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h14m11s)

1. Accédez à la **Vue Administrateur** → cliquez sur l'icône **Champs liés**.
2. Ajoutez le champ **Alias** existant à la vue administrateur des salutations.
3. Enregistrez et fermez.

Cela crée des URL basées sur les slugs pour chaque message d'accueil.

---

<a id="15-testing-data-and-display"></a>
## 15. Test des données et de l'affichage

[01:20:46](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h20m46s)
Utilisez un var_dump PHP dans la vue du site pour confirmer :

```php
<?php var_dump($this->items); ?>
```

Recompilez et réinstallez. Vous verrez des limaces pour chaque élément.

---

<a id="16-linking-records-using-helper-route"></a>
## 16. Lier des enregistrements à l'aide de la route d'assistance

[01:22:36](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h22m36s)
Chaque vue de site dispose d'un itinéraire d'assistance.
Utilisez le modèle suivant pour créer des liens de manière dynamique :

```php
<a href="<?php echo JRoute::_(
  Hello_worldHelperRoute::getGreetedRoute($item->slug)
); ?>">
  <?php echo $item->name; ?>
</a>
```

Compilez et réinstallez.

---

<a id="17-managing-permissions"></a>
## 17. Gestion des autorisations

[01:41:03](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h41m03s)
Définissez les autorisations pour contrôler l'accès **Modifier**, **Créer** et **Afficher**.

Go to:

* **Options des composants → Autorisations**
* Ajuster par groupe :

  * `Greetings (site) access`
  * `Greeted (site) access`
  * `core.edit`
  * `core.create`

Lorsque l'autorisation est accordée :

* Les boutons Modifier apparaissent.
* Les boutons Créer sont visibles.
* Les utilisateurs non autorisés voient les messages de restriction d'accès.

Exemple d'extrait PHP pour le bouton d'édition contrôlé par autorisation :

```php
<?php if ($canDo->get('core.edit')) : ?>
  <a href="<?php echo $editLink; ?>">
    <i class="icon-pencil"></i>
  </a>
<?php endif; ?>
```

---

<a id="18-editing-and-creating-items-from-the-frontend"></a>
## 18. Modification et création d'éléments à partir du frontend

[01:34:52](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h34m52s)
Activer l'édition frontale :

1. Ajoutez des vérifications PHP pour l'autorité des utilisateurs dans vos vues de liste et de site unique.
2. Insérez une icône de lien d'édition si les autorisations le permettent.

Exemple d'extrait :

```php
<?php if ($this->user->authorise('core.edit', 'com_hello_world')) : ?>
  <a href="<?php echo $editLink; ?>"><i class="icon-pencil"></i></a>
<?php endif; ?>
```

Ajoutez le bouton "Créer" avec des vérifications d'autorisation similaires.

---

<a id="19-compile-and-test-again"></a>
## 19. Compiler et tester à nouveau

[01:43:17](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h43m17s)
Recompilez après chaque modification et réinstallez le composant.
Testez les éléments suivants :

* Afficher la liste de salutations.
* Ouvrez un seul message d'accueil.
* Modifiez et créez de nouvelles salutations.
* Confirmez que les autorisations se comportent comme prévu.

---
