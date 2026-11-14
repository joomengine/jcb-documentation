> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-add-a-form-to-a-site-view"></a>
# Comment ajouter un formulaire à une vue de site

<a id="introduction"></a>
## Introduction

> [00:00:10](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h00m10s)

Dans ce didacticiel, nous montrons comment **ajouter un formulaire à une vue de site** dans Joomla Component Builder (JCB).
Le processus suit la **structure MVC** de Joomla et le flux de travail de génération automatisé de JCB, où les vues de site sont assemblées à partir d'requêtes dynamiques, de modèles, de mises en page, d'espaces réservés de code personnalisé facultatifs et de toutes les bibliothèques frontales que vous attachez pour l'interactivité.

Bien qu'il soit possible d'ajouter manuellement un formulaire à une vue de site, **la meilleure pratique de Joomla** consiste à utiliser une **vue administrateur comme vue de site**, car l'architecture de base de Joomla s'attend à ce que les soumissions de formulaires proviennent de ces vues.

---

<a id="1-best-practice-use-an-admin-view-as-a-site-view"></a>
## 1. Bonne pratique : utiliser une vue administrateur comme vue du site

> [00:00:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h00m37s)

Lorsque vous souhaitez stocker les données d'un formulaire dans la base de données, la méthode recommandée est la suivante :

1. **Créez une vue administrateur** contenant la structure du formulaire et du tableau.
2. **Activez l'option "Créer une vue de modification du site"** dans JCB.
   Cela rend automatiquement la vue administrateur accessible depuis le **frontend** en tant que vue du site.

**Pourquoi il s'agit d'une bonne pratique :**

* Suit la structure MVC native de Joomla.
* Garantit que le code généré gère correctement la validation, l'enregistrement et les autorisations.
* Réduit le risque de gestion de formulaires non sécurisée ou non prise en charge.

---

<a id="2-building-the-edit-link-in-your-site-view"></a>
## 2. Création du lien Modifier dans la vue de votre site

> [00:01:11](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h01m11s)

Pour accéder à la zone d'édition de votre vue du site, vous avez besoin d'un **Modifier le lien**.
Ce lien n'est pas généré automatiquement, vous devez l'ajouter manuellement.

**Mesures:**

1. Accédez aux **GETs dynamiques** dans JCB.
2. Ouvrez le GET associé à votre vue de site (par exemple, `looks`).
3. Dans le script GET dynamique, récupérez les **actions** et les **permissions**.
4. Créez un lien de modification conditionnelle à l'aide de `JRoute` si l'utilisateur dispose de l'autorisation `core.edit`.

Exemple d'extrait (de la vidéo) :

```php
if ($canEdit) {
    $item->edit_link = JRoute::_('index.php?option=com_example&task=item.edit&id=' . $item->id);
} else {
    $item->edit_link = '';
}
```

*Astuce :* Garder cette logique à l'intérieur du modèle (via Dynamic GET) permet de maintenir la séparation MVC.

---

<a id="3-using-existing-pagination-form"></a>
## 3. Utilisation du formulaire de pagination existant

> [00:02:54](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h02m54s)

Si votre vue de site utilise déjà la **pagination**, Joomla inclut automatiquement une balise `<form>` autour de la mise en page de votre liste.
Cela signifie que vous disposez déjà d’un formulaire, pas besoin d’en ajouter un autre.

**Étapes pour confirmer :**

1. Dans JCB, ouvrez votre **Vue du site** (par exemple, `Looks`).
2. Assurez-vous que **Pagination** est défini sur **Oui**.
3. Compilez et inspectez le HTML généré :

   ```html
   <form action="index.php?option=com_example&view=looks" method="post" name="adminForm" id="adminForm">
       ...
       <input type="hidden" name="task" value="" />
       <input type="hidden" name="form_token" value="1" />
   </form>
   ```4. Vous pouvez désormais simplement **ajouter des boutons** ou des **entrées masquées** dans ce formulaire pour capturer et traiter les soumissions.

*Vous disposez déjà d'une protection CSRF via le jeton de formulaire de Joomla.*

---

<a id="4-adding-a-custom-submit-button"></a>
## 4. Ajout d'un bouton de soumission personnalisé

> [00:05:14](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h05m14s)

Pour déclencher des actions de formulaire personnalisées, ajoutez un bouton via la **configuration des boutons** de JCB.

**Mesures:**

1. Accédez à votre **Vue du site** dans JCB.
2. Ajoutez un nouveau **Bouton** :

* **Nom :** `Submit`
   * **Icône :** par exemple, `save`
   * **Méthode de tâche/contrôleur :** `saveMyStuff`
   * **Contrôleur cible :** le contrôleur de votre vue (par exemple, `looks`)
3. Ajoutez l'**Option personnalisée** (espace réservé au code) pour positionner votre bouton dans la présentation du formulaire.

Une fois compilé, JCB :

* Insérez le bouton dans le formulaire existant.
* Générez ou mettez à jour les fichiers de contrôleur et de modèle associés.

---

<a id="5-creating-the-controller-method"></a>
## 5. Création de la méthode du contrôleur

> [00:06:55](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h06m55s)

Après avoir ajouté le bouton, JCB génère un **contrôleur** avec votre méthode personnalisée.

Structure typique :

```php
public function saveMyStuff() {
    JSession::checkToken() or jexit('Invalid Token');

    $app = JFactory::getApplication();
    $model = $this->getModel('Looks');
    $data  = $this->input->get('jform', array(), 'array');

    if (!$model->validate($data)) {
        $app->enqueueMessage('Validation failed', 'error');
        $app->setUserState('com_example.edit.looks.data', $data);
        $this->setRedirect(JRoute::_('index.php?option=com_example&view=looks', false));
        return false;
    }

    if (!$model->save($data)) {
        $app->enqueueMessage('Save failed', 'error');
        return false;
    }

    $app->enqueueMessage('Data saved successfully');
    $this->setRedirect(JRoute::_('index.php?option=com_example&view=looks', false));
}
```

**Important :** Effectuez toujours la validation des jetons et la désinfection des entrées pour éviter les vulnérabilités.

---

<a id="6-extending-the-model"></a>
## 6. Extension du modèle

> [00:09:43](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h09m43s)

Votre contrôleur appelle des méthodes de modèle telles que :

* `getForm()`
* `validate()`
* `save()`

Vous devez les implémenter ou les étendre dans votre fichier **Modèle** (`models/looks.php`).

Si vous utilisez des champs dynamiques ou personnalisés, vous pouvez créer votre formulaire de manière dynamique via du code ou XML.

---

<a id="7-alternative-method-add-a-separate-form"></a>
## 7. Méthode alternative : ajouter un formulaire séparé

> [00:16:29](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h16m29s)

Pour les champs de recherche ou les petits formulaires de soumission, vous pouvez insérer un **deuxième formulaire** manuellement au-dessus du contenu principal.

**Mesures:**

1. Accédez à l'onglet **PHP personnalisé** de votre vue de site dans JCB.
2. Ajoutez PHP et HTML pour créer un formulaire autonome :

   ```php
   <?php echo '<form id="searchForm" method="post" action="index.php?option=com_example&task=search">'; ?>
       <input type="text" name="query" placeholder="Search..." />
       <button type="submit">Search</button>
   <?php echo '</form>'; ?>
   ```3. Compilez et testez.
   Ce formulaire apparaît au-dessus de celui existant sans conflits.

---

<a id="8-how-jcb-compiles-controller--model-code"></a>
## 8. Comment JCB compile le code du contrôleur et du modèle

> [00:14:32](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h14m32s)

Lorsque vous compilez, JCB :

* Crée ou met à jour le contrôleur (`controllers/looks.php`).
* Ajoute automatiquement votre nouvelle tâche (par exemple, `saveMyStuff`).
* Met à jour le modèle avec `getForm()` et les méthodes associées.

Vous pouvez le vérifier dans les fichiers de composants générés après la compilation.

---

<a id="9-understanding-field-building-the-jcb-way"></a>
## 9. Comprendre la construction sur le terrain à la manière de JCB

> [00:21:38](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h21m38s)

Le compilateur de JCB utilise les **objets de champ de formulaire** de Joomla pour créer des formulaires de manière dynamique.

<a id="helper-getfieldobject"></a>
### Assistant : `getFieldObject()`

Cette méthode d'assistance automatise la création de champs en prenant :

* **Attributs** (type, nom, étiquette, description, etc.)
* **Valeur par défaut**
* **Options**

Il construit un champ XML Joomla valide et le charge via :

```php
$field = JFormHelper::loadFieldType($attributes['type']);
$field->setup($xmlField, $value);
return $field;
```

Cela garantit une compatibilité totale avec le système de gestion de champs natif de Joomla.

---

<a id="10-accessing-the-compilers-custom-admin-view-example"></a>
## 10. Accès à l'exemple de vue d'administration personnalisée du compilateur

> [00:26:20](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h26m20s)

Vous pouvez étudier le composant **Compiler** de JCB pour un exemple réel de rendu de formulaire dynamique.

**Mesures:**

1. Dans JCB, importez le **composant JCB lui-même** via *Import JCB Package*.
2. Ouvrez le **Compilateur (vue d'administration personnalisée)**.
3. Consultez l'onglet PHP pour voir comment JCB :

* Charge les champs dynamiquement.
   * Utilise `JText::_()` pour les chaînes de langue.
   * Affiche les champs et les contrôles dans un formulaire Joomla standard.

Il s'agit d'une référence idéale pour créer vos propres formulaires de site dynamiques.

---

<a id="summary"></a>
## Résumé

> [00:29:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h29m37s)

**L'ajout d'un formulaire à une vue du site** dans JCB peut être effectué de deux manières principales :

| Méthode | Descriptif | Idéal pour |
| ----------------------------------- | ------------------------------------------------------------------------ | -------------------------- |
| **1. Utiliser le formulaire de pagination existant** | Ajoutez des boutons ou des champs dans la structure de formulaire existante de Joomla.           | Soumissions de données pleine page |
| **2. Formulaire personnalisé ci-dessus ** | Ajoutez un formulaire séparé via l'onglet PHP pour les tâches légères (recherche, filtrage). | Interactions rapides |

---

<a id="pro-tips"></a>
## Conseils de pro

* Toujours **valider et désinfecter** les entrées à l'aide de la validation de modèle de Joomla.
* Utilisez `JSession::checkToken()` pour empêcher les attaques CSRF.
* Gardez la logique dans les contrôleurs et les modèles, pas dans les vues.
* Étudiez la vue du compilateur de JCB pour obtenir des exemples de bonnes pratiques.
* Évitez de créer plusieurs formulaires sauf si cela est absolument nécessaire.

---

<a id="conclusion"></a>
## Conclusion

> [00:30:00](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h30m00s)

En suivant ces étapes, vous pouvez ajouter des formulaires en toute sécurité et efficacement à vos vues de site JCB, en tirant parti de la structure MVC de Joomla et de l'automatisation de JCB tout en maintenant la sécurité et une architecture propre.

---
