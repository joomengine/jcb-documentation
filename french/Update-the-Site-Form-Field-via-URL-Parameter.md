> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="update-the-site-form-field-via-url-parameter"></a>
# Mettre à jour le champ du formulaire du site via le paramètre URL

<a id="overview"></a>
## Aperçu

Dans ce didacticiel, nous apprendrons comment **ajouter un formulaire à une vue de site** dans Joomla Component Builder (JCB), gérer sa soumission via un **contrôleur** et le lier dynamiquement au **modèle** pour validation et enregistrement.
Nous verrons également comment JCB permet de générer automatiquement une grande partie du code nécessaire - y compris les **boutons**, les **contrôleurs** et les **méthodes de modèle** - tout en gardant la structure MVC intacte.

> **[00:00:10](https://www.youtube.com/watch?v=UVICsD82oWk&t=10s)**

---

<a id="1-using-an-admin-view-as-a-site-view"></a>
## 1. Utiliser une vue administrateur comme vue du site

> **[00:00:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=37s)**

La meilleure pratique dans Joomla consiste à utiliser une **Vue Administrateur comme Vue du Site** pour les formulaires qui stockent des données dans la base de données.

<a id="why-this-is-recommended"></a>
### Pourquoi ceci est recommandé

* **La structure MVC de Joomla** est optimisée pour cette approche.
* La même logique de vue Admin peut être étendue pour le frontend.
* La soumission des données (enregistrement dans la base de données) est déjà intégrée à l'architecture d'administration.

Pour créer une vue de site à partir d'une vue administrateur :

1. Ouvrez votre composant dans **JCB**.
2. Localisez votre **Vue administrateur**.
3. Cochez l'option **"Créer une vue de site pour cette vue d'administration"**.
4. JCB génère automatiquement la **Vue du site** correspondante.

---

<a id="2-creating-an-edit-link-for-site-view"></a>
## 2. Création d'un lien de modification pour la vue du site

> **[00:01:11](https://www.youtube.com/watch?v=UVICsD82oWk&t=71s)**

La zone d'édition du site n'est pas générée automatiquement ; vous devez créer un **lien d'édition dynamique** manuellement.

<a id="steps"></a>
### Étapes :

1. Accédez aux **GETs dynamiques** dans JCB.
2. Ouvrez la requête GET pour la vue de votre site (par exemple, `Looks`).
3. Ajoutez du code à :

* Récupérer les **autorisations utilisateur** (par exemple, canEdit).
   * Si c'est vrai, créez un lien avec `JRoute`.
   * Incluez la tâche et l'itinéraire cible.

Exemple d'extrait (du didacticiel) :

```php
if ($canEdit) {
  $link = JRoute::_('index.php?option=com_yourcomponent&task=look.edit&id=' . $item->id);
} else {
  $link = '';
}
```

> *Conseil :* Séparez la modélisation des données de la logique d'affichage : créez des liens dans la couche modèle, pas dans la vue.

---

<a id="3-using-the-existing-form-with-pagination"></a>
## 3. Utiliser le formulaire existant avec la pagination

> **[00:03:22](https://www.youtube.com/watch?v=UVICsD82oWk&t=202s)**

Si la vue de votre site possède déjà une **pagination**, JCB génère automatiquement une balise `<form>` autour de la liste.

Vous **n'avez pas besoin d'ajouter un autre formulaire** - ajoutez simplement des entrées ou des boutons à l'intérieur.

<a id="how-it-works"></a>
### Comment ça marche

* Pagination = création automatique de `<form>`.
*Le formulaire comprend :

* Attributs `name` et `id`.
  * Un `form token` pour la sécurité.
  * `action` pointant vers votre composant.

Exemple de structure générée :

```html
<form action="index.php?option=com_yourcomponent" method="post" id="adminForm" name="adminForm">
  <!-- Your fields and buttons here -->
  <?php echo JHtml::_('form.token'); ?>
</form>
```

Vous pouvez insérer votre propre bouton de soumission :

```html
<button type="submit" class="btn btn-success">Submit</button>
```

Utilisez ensuite JavaScript ou la logique du contrôleur pour traiter la tâche de formulaire.

---

<a id="4-adding-a-custom-button-in-jcb"></a>
## 4. Ajout d'un bouton personnalisé dans JCB

> **[00:05:38](https://www.youtube.com/watch?v=UVICsD82oWk&t=338s)**

Vous pouvez ajouter un **bouton personnalisé** directement dans JCB.

<a id="steps-1"></a>
### Étapes :

1. Ouvrez votre **Vue du site**.
2. Dans **Boutons**, cliquez sur **Ajouter un bouton**.
3. Définir :

* **Nom du bouton :** par exemple, `Submit`
   * **Icône :** choisissez dans la liste
   * **Méthode du contrôleur cible :** par exemple, `saveMyStuff`
   * **Type de bouton :** Par défaut (laisser inchangé)
4. Utilisez **Option personnalisée → Copier → Coller** pour contrôler le placement des boutons.

Cela configure automatiquement :

* Le **contrôleur** et le **nom de la méthode**.
* Le bouton **barre d'outils**.
* Le **lien du modèle** correspondant.

Après la compilation, vérifiez le généré :

* `/controllers/look.php` - nouveau contrôleur avec votre méthode.
* `/models/look.php` - inclut les méthodes de modèle (par exemple, `getForm`, `validate`, `save`).

---

<a id="5-understanding-the-controller-logic"></a>
## 5. Comprendre la logique du contrôleur

> **[00:07:18](https://www.youtube.com/watch?v=UVICsD82oWk&t=438s)**

Chaque soumission de formulaire déclenche une **méthode de contrôleur**.

Poignées du contrôleur :

1. **Validation des jetons** pour la sécurité.
2. **Récupération d'entrée** à partir de `JInput`.
3. **Accès au modèle** via `getModel()`.
4. **Validation et sauvegarde du formulaire**.
5. **Redirections** une fois terminé.

<a id="example-flow"></a>
### Exemple de flux :

```php
public function saveMyStuff() {
  JSession::checkToken() or jexit('Invalid Token');
  $app = JFactory::getApplication();
  $model = $this->getModel('Look');
  $data = $app->input->get('jform', [], 'array');

  $form = $model->getForm($data, false);
  $validated = $model->validate($form, $data);

  if ($validated === false) {
    $errors = $model->getErrors();
    foreach ($errors as $error) {
      $app->enqueueMessage($error, 'warning');
    }
    $app->setUserState('com_yourcomponent.edit.look.data', $data);
    $this->setRedirect(JRoute::_('index.php?option=com_yourcomponent&view=look&layout=edit', false));
    return false;
  }

  $model->save($validated);
  $app->enqueueMessage('Saved successfully', 'message');
  $this->setRedirect(JRoute::_('index.php?option=com_yourcomponent&view=looks', false));
}
```

> *Toujours inclure les contrôles de validation et CSRF.*

---

<a id="6-model-integration"></a>
## 6. Intégration du modèle

> **[00:10:17](https://www.youtube.com/watch?v=UVICsD82oWk&t=617s)**

Vous devrez ajouter manuellement les méthodes compatibles à votre **modèle** :

* `getForm()`
* `validate()`
* `save()`

Pour les formulaires dynamiques (et non XML statiques), JCB prend en charge les formulaires **XML générés au moment de l'exécution**.

---

<a id="7-example-of-dynamic-form-xml-builder"></a>
## 7. Exemple de générateur XML de formulaire dynamique

> **[00:11:31](https://www.youtube.com/watch?v=UVICsD82oWk&t=691s)**

Le composant compilateur de JCB montre comment **créer dynamiquement des champs de formulaire XML**.

```php
$field = $helper->getFieldObject($attributes, $defaultValue, $options);
```

<a id="helper-workflow"></a>
### Flux de travail d'assistance

* Crée une structure XML.
* Ajoute des attributs et des options.
* Charge dynamiquement le type de champ Joomla.

Utilisez cette approche pour créer des structures de champ dynamiques au sein de vos modèles.

---

<a id="8-custom-php-in-site-view"></a>
## 8. PHP personnalisé dans la vue du site

> 🕒 **[00:16:54](https://www.youtube.com/watch?v=UVICsD82oWk&t=1014s)**

Pour plus de contrôle, utilisez le **script de vue PHP personnalisé**.

<a id="steps-2"></a>
### Étapes :

1. Ouvrez votre **Vue du site**.
2. Dans l'**onglet PHP**, ajoutez votre script personnalisé.
3. Insérez votre formulaire au-dessus du formulaire par défaut en utilisant la syntaxe PHP :

   ```php
   ?> 
   <form id="myCustomForm">
     ...
   </form>
   <?php
   ```4. Assurez-vous que les formulaires `name` et `id` sont uniques.

---

<a id="9-best-practices-for-form-building-in-jcb"></a>
## 9. Meilleures pratiques pour la création de formulaires dans JCB

> 🕒 **[00:21:38](https://www.youtube.com/watch?v=UVICsD82oWk&t=1298s)**

* Utilisez toujours les **classes d'assistance de JCB** (`getFieldObject`, etc.).
* Laissez **Joomla gérer le rendu et la gestion des jetons**.
* Conservez la logique du formulaire dans la **structure MVC**.
* Validez chaque entrée dans le **contrôleur et le modèle**.
* Désinfectez correctement les entrées de l'utilisateur.

---

<a id="10-using-jcbs-own-compiler-as-a-reference"></a>
## 10. Utiliser le propre compilateur de JCB comme référence

> **[00:25:48](https://www.youtube.com/watch?v=UVICsD82oWk&t=1548s)**

Vous pouvez **importer le composant JCB dans JCB** lui-même pour étudier comment son compilateur gère les formulaires.

1. Accédez à **Composants → Composants Joomla**.
2. Cliquez sur **Importer le package JCB**.
3. Sélectionnez le package `Component Builder`.
4. Ajoutez votre **clé de licence**.
5. Poursuivez l'importation.

Ouvrez la **vue du compilateur** et étudiez :

* Méthodes PHP qui génèrent des champs.
* Comment les étiquettes et les chaînes de langue sont gérées.
* Comment la fonction `JText::_()` mappe les étiquettes aux constantes de langage.

---

<a id="summary"></a>
## Résumé

| Tâche | Zone | Descriptif |
| ------------------ | ---------- | ---------------------------------------------------------- |
| Créer un formulaire de site | Vue du site | Activer le formulaire en réutilisant le formulaire de pagination |
| Ajouter un bouton | Interface utilisateur des boutons JCB | Créer un bouton « Soumettre » lié au contrôleur |
| Contrôleur de construction | Automatique/Manuel | Gère la soumission, la validation, la redirection |
| Ajouter une logique de modèle | Modèle | Inclut `getForm()`, `validate()`, `save()` |
| Utiliser des champs dynamiques | Aide | Utiliser `getFieldObject()` pour la génération XML |
| Ajouter du PHP personnalisé | Onglet PHP | Insérer le balisage du formulaire au-dessus/au-dessous de la liste |
| Tester et compiler | Compilateur | Construire et installer pour tester les fonctionnalités |

---

<a id="pro-tips"></a>
## Conseils de pro

* Utilisez les **Boutons JCB** pour générer rapidement des échafaudages.
* Compilez toujours après avoir apporté des modifications à la structure.
* Évitez de dupliquer les balises `<form>` dans les listes paginées.
* Consultez la **vue d'administration du compilateur** de JCB pour connaître les modèles de rendu de formulaire avancés.
* Utilisez des **constantes de langage** pour les étiquettes de champ (`COM_COMPONENT_FIELD_LABEL`).

---

<a id="closing-notes"></a>
## Notes de clôture

> **[00:29:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=1777s)**

Cette méthode garantit :

* Formulaires entièrement conformes à MVC.
* Intégration plus propre avec Joomla.
* Génération automatisée de code de contrôleur/modèle.
* Gestion des formulaires frontaux maintenables et sécurisés.

---
