> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-add-custom-buttons-in-jcb-to-your-component-admin-area"></a>
# Comment ajouter des boutons personnalisés dans JCB à la zone d'administration de vos composants

Ce guide explique comment **ajouter des boutons personnalisés** à vos composants Joomla Component Builder (JCB) - à la fois dans les **Vues de liste** et **Vues d'édition** - en utilisant l'interface de JCB sans remplacements PHP personnalisés.
Vous découvrirez également comment ces boutons s'intègrent aux **contrôleurs, modèles** et au **système d'autorisation** de Joomla, selon les principes MVC.

> *Basé sur le didacticiel vidéo : [Comment ajouter des boutons personnalisés dans JCB à la zone d'administration de vos composants](https://www.youtube.com/watch?v=VyBxWpJWb40)*
> (*Cliquez sur les horodatages pour accéder à ce moment dans la vidéo.*)

---

<a id="overview"></a>
## Aperçu

[00:00:00](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h00m00s)

Ce didacticiel montre comment ajouter des boutons :

* La barre d'outils **Affichage de la liste d'administration**, ou
* La barre d'outils **Modifier la vue**.

Ces boutons vous permettent de déclencher des méthodes de contrôleur personnalisées (par exemple, rediriger les utilisateurs, exécuter une logique personnalisée ou modifier des données) directement depuis l'interface d'administration de Joomla, sans modification manuelle du code.

---

<a id="1-preparing-the-environment"></a>
## 1. Préparer l'environnement

[00:00:38](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h00m38s)

1. Ouvrez un **site Joomla propre** avec JCB installé.
2. Assurez-vous que votre **composant de démonstration** est déjà mappé et installé.
3. Ouvrez votre composant à partir du panneau **Joomla Administrator**.
4. Accédez à n'importe quelle vue (par exemple, `Looks`) pour confirmer qu'elle affiche les boutons Joomla standard (`New`, `Edit`, `Publish`, `Unpublish`, etc.).

Votre objectif sera d'ajouter de **nouveaux boutons personnalisés** ici en utilisant JCB.

---

<a id="2-navigating-to-custom-buttons-in-jcb"></a>
## 2. Navigation vers les boutons personnalisés dans JCB

[00:01:19](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h01m19s)

1. Dans JCB, accédez à **Vues administrateur**.
2. Ouvrez la vue souhaitée (par exemple, `Look`).
3. Localisez la section **Boutons personnalisés**.
4. Cliquez sur **"Oui"** lorsqu'on vous demande d'ajouter un bouton personnalisé.

---

<a id="3-understanding-the-mvc-relationship"></a>
## 3. Comprendre la relation MVC

[00:02:05](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h02m05s)

Chaque vue d'administration dans JCB est soutenue par :

* Un contrôleur et un modèle **Vue Liste**, et
* Un contrôleur et un modèle **Modifier la vue**.

En fonction de l'endroit où votre bouton apparaît, JCB placera automatiquement la méthode PHP dans les bons fichiers de contrôleur et de modèle :

* Les boutons de la **vue liste** affectent plusieurs enregistrements.
* Les boutons de la **vue d'édition** agissent sur un seul élément.

> **Astuce :** La familiarité avec l'API MVC de Joomla vous aide à comprendre comment la logique PHP générée s'articule.

---

<a id="4-creating-a-custom-button"></a>
## 4. Création d'un bouton personnalisé

[00:03:07](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h03m07s)

Suivez ces étapes pour ajouter votre premier bouton personnalisé :

1. Dans **Boutons personnalisés**, cliquez sur **"Ajouter"**.
2. Définir :

* **Icône :** Choisissez parmi les icônes *Icomoon* par défaut de Joomla.
   * **Nom :** Par exemple, `Test`.
   * **Nom de la méthode du contrôleur :** Par exemple, `getTested`.
3. **Type d'affichage cible :** Choisissez l'endroit où le bouton apparaît :

* `list`
   * `single`
   * `both`
4. **Tapez :**

* `Function` - s'exécute directement lorsque vous cliquez dessus.
   * `Selection` - nécessite que les lignes sélectionnées transmettent les identifiants.
   * `Default` - similaire à la sélection mais avec un comportement flexible.

Enregistrez votre bouton.

---

<a id="5-writing-the-controller-method"></a>
## 5. Écrire la méthode du contrôleur

[00:05:05](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h05m05s)

Une fois compilé, JCB crée automatiquement la méthode PHP dans le fichier de contrôleur approprié.

Exemple:

```php
public function getTested()
{
    // Verify request origin
    if (!JSession::checkToken()) {
        jexit('Invalid Token');
    }

    // Redirect to dashboard
    $this->setRedirect(JRoute::_('index.php?option=com_demo', false));
}
```

> **Comment JCB gère les blocs vides :**
> Si aucun code n'est ajouté, JCB insère des barres obliques `//` pour conserver la structure.

Compilez et installez votre composant.
Accédez à **Composants → Démo → Looks** - votre nouveau bouton **Test** apparaît.
En cliquant dessus, vous serez redirigé vers le tableau de bord.

---

<a id="6-adding-a-button-to-the-edit-view"></a>
## 6. Ajout d'un bouton à la vue d'édition

[00:07:05](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h07m05s)

Pour créer un bouton dans la **Vue Modifier** :

1. Ajoutez un autre bouton personnalisé.

* **Cible :** `single`
   * **Nom :** `Work`
   * **Méthode du contrôleur :** `getDone`
   * **Type :** `Default`
2. Dans votre méthode de contrôleur, JCB insère :

```php
public function getDone()
{
    // Access the model
    $model = $this->getModel();
    $data  = $model->getData();

    // Perform your logic, then redirect or return status
}
```

Tu peux:

* Valider les données des articles,
* Effectuer des opérations dessus,
* Utilisez `$model->save($data)` pour stocker les valeurs mises à jour.

---

<a id="7-validating-and-triggering-the-model"></a>
## 7. Valider et déclencher le modèle

[00:09:33](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h09m33s)

Dans votre contrôleur :

1. Vérifiez que l'élément est **enregistré** (`$data->id > 0`).
2. Vérifiez que les champs nécessaires sont définis (par exemple, `$data->name`).
3. Ensuite seulement, appelez une méthode de modèle personnalisée.

Exemple:

```php
if ($data->id > 0 && !empty($data->name)) {
    $model->performWork($data);
} else {
    $this->setMessage('Missing required data', 'error');
}
```

---

<a id="8-handling-logic-in-the-model"></a>
## 8. Gestion de la logique dans le modèle

[00:10:39](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h10m39s)

A l'intérieur du modèle :

```php
public function performWork($data)
{
    // Perform logic and return success or failure
    if ($this->save($data)) {
        return true;
    }
    return false;
}
```

Renvoyez `true` ou `false` pour déclencher des messages Joomla dans le contrôleur.

> **Meilleure pratique :** Utilisez le `enqueueMessage()` de Joomla pour afficher les commentaires des utilisateurs.

---

<a id="9-compiling-and-testing"></a>
## 9. Compilation et tests

[00:13:08](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h13m08s)

1. Enregistrez votre vue d'administration dans JCB.
2. Compilez et installez le composant.
3. Testez :

* **Vue en liste :** Le bouton "Test" redirige correctement.
   * **Modifier la vue :** Le bouton "Travail" déclenche votre méthode de modèle.
4. Inspectez les fichiers générés :

* `controllers/looks.php` → contrôleur de vue de liste
   * `controllers/look.php` → modifier le contrôleur de vue
   * `models/look.php` → modèle correspondant

---

<a id="10-adding-the-same-button-to-both-list-and-edit-views"></a>
## 10. Ajout du même bouton aux vues de liste et d'édition

[00:17:29](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h17m29s)

Vous pouvez attribuer un bouton pour qu'il apparaisse dans **les deux** zones :

1. Modifiez votre bouton dans JCB.
2. Remplacez **Type de vue cible** par `Both`.
3. Enregistrez et compilez à nouveau.

Après l'installation :

* Le bouton apparaît dans les deux vues.
* JCB ajoute automatiquement le code nécessaire à `view.html.php` dans la méthode de génération de barre d'outils.

---

<a id="11-permissions-integration"></a>
## 11. Intégration des autorisations

[00:19:43](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h19m43s)

JCB intègre automatiquement les contrôles d'autorisation.
Chaque bouton personnalisé possède un **commutateur ACL** qui respecte les paramètres d'autorisation de Joomla.

Si un utilisateur n'a pas l'autorisation :

* Le bouton est masqué dans la barre d'outils.
* Même l'exécution directe d'URL est bloquée au niveau du contrôleur.

> Utilisez toujours la vérification ACL de Joomla :

```php
if (!JFactory::getUser()->authorise('core.edit', 'com_demo'))
{
    throw new Exception('Not permitted', 403);
}
```

---

<a id="12-summary-and-best-practices"></a>
## 12. Résumé et bonnes pratiques

[00:20:53](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h20m53s)

Vous avez maintenant appris à :

* Ajoutez des **boutons personnalisés** pour répertorier et modifier les vues dans JCB.
* Définissez la **logique du contrôleur et du modèle** pour eux.
* Gérez les **autorisations** en toute sécurité.
* Réutilisez cette fonctionnalité pour les automatisations, les validations et les raccourcis.

> **Conseil :**
> Expérimentez avec différents types et méthodes de boutons - JCB gère l'intégration Joomla MVC, vous permettant de vous concentrer uniquement sur votre logique personnalisée.

---

<a id="key-takeaways"></a>
### Points clés à retenir

| Étape | Descriptif |
| ---- | ---------------------------------------------------------- |
| 1 | Choisissez votre vue cible et le comportement des boutons |
| 2 | Définir la méthode du contrôleur dans JCB |
| 3 | Ajouter une logique à l'intérieur du contrôleur et du modèle |
| 4 | Compiler et tester dans Joomla |
| 5 | Implémenter des contrôles d'autorisation |

---
