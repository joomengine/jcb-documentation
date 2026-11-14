> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-integrate-the-create-user-helper-method-in-your-components"></a>
# Comment intégrer la méthode Create User Helper dans vos composants

**Source du didacticiel :** [Joomla Component Builder Tutorial Series](https://www.youtube.com/watch?v=ckFakaQ90JY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
---

<a id="1-overview"></a>
## 1. Aperçu

[00:00:00](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h00m00s)

La **Méthode d'assistance Créer un utilisateur** permet à votre composant Joomla de créer des utilisateurs Joomla de manière dynamique à partir des vues ou des actions de votre composant. Cela se fait à l'aide d'une extension JCB Helper Class intégrée qui ajoute des méthodes réutilisables accessibles à la fois sur le front-end et le back-end de votre composant.

Cette intégration est utile pour les composants tels que les gestionnaires de tâches, les systèmes d'adhésion ou les répertoires d'experts, partout où un processus de création d'utilisateurs personnalisé est nécessaire.

---

<a id="2-understanding-the-helper-class"></a>
## 2. Comprendre la classe Helper

[00:00:32](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h00m32s)

Chaque composant généré par JCB contient une **Classe d'assistance**, une pour le côté administrateur et une pour le côté site.

Vous pouvez le localiser dans :

```
/administrator/components/com_expertdatabase/helpers/expertdatabase.php
```

Ce fichier définit la classe principale `expertdatabaseHelper`.
Il est **automatiquement chargé** par Joomla! à chaque fois que votre composant s'exécute, garantissant que toutes les fonctions d'assistance sont disponibles dans le monde entier.

[00:01:28](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h01m28s)

Dans l'interface d'administration JCB :

1. Ouvrez **Component Builder Dashboard** → **Composants** → sélectionnez votre composant.
2. Faites défiler jusqu'à **Bibliothèque et assistants**.
3. Localisez le commutateur **Ajouter une méthode d'assistance à la création d'un utilisateur** et activez-le **ON**.

[00:02:11](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h02m11s)

Cette commande indique à JCB d'inclure automatiquement la fonction "Créer un utilisateur" dans votre classe d'assistance lors de la compilation pour les zones de site et d'administration.

---

<a id="3-the-create-user-function"></a>
## 3. La fonction Créer un utilisateur

[00:03:00](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h03m00s)

Une fois activé, JCB ajoute une méthode comme celle-ci à votre classe d'assistance :

```php
public static function createUser($new)
```

Vous pouvez l'appeler en utilisant :

```php
expertdatabaseHelper::createUser($new);
```

Où `$new` est un **tableau** contenant les données d'enregistrement des utilisateurs :

```php
$new = array(
    'username'  => 'testing123',
    'name'      => 'Testing 123',
    'email'     => 'testing123@vdm.io',
    'password'  => 'mySecretPass',
    'password2' => 'mySecretPass'
);
```

[00:03:26](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h03m26s)

La méthode d'assistance exploite le **Modèle d'enregistrement d'utilisateur** intégré de Joomla, créant l'utilisateur via l'API Joomla standard.

Cela simplifie le processus mais **n'attribue pas automatiquement les utilisateurs à des groupes**, qui doivent être gérés manuellement après la création.

---

<a id="4-using-the-create-user-function-in-a-view"></a>
## 4. Utilisation de la fonction Créer un utilisateur dans une vue

[00:04:30](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h04m30s)

Utilisons la vue d'administration **Experts** comme exemple.

Lors de la création d'un nouvel Expert :

1. Accédez à **Base de données d'experts → Experts → Nouveau**.
2. Vous trouverez un champ intitulé **Expert**, qui vous permet de sélectionner des utilisateurs au sein d'un groupe spécifique.
3. En dessous, un bouton **Créer un utilisateur** apparaît.

[00:05:26](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h05m26s)

Cela ouvre une fenêtre modale dans laquelle vous pouvez saisir :

* Nom d'utilisateur
* Nom
* Courriel
* Mot de passe

Après la soumission, Joomla envoie un message de réussite confirmant que le nouvel utilisateur a été créé et que les informations de connexion ont été envoyées par courrier électronique.

[00:06:05](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h06m05s)

Une fois créé, le nouvel utilisateur peut être sélectionné dans le champ de liste des utilisateurs du formulaire Expert.

> **Astuce :** Les noms d'utilisateur Joomla ne peuvent généralement pas contenir de chiffres, sauf autorisation spécifique dans votre configuration ou remplacement via un plugin.

---

<a id="5-integrating-create-user-via-ajax"></a>
## 5. Intégration de Créer un utilisateur via AJAX

[00:09:30](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h09m30s)

Pour créer des utilisateurs de manière dynamique sans recharger la page, JCB prend en charge l'**intégration AJAX**.

Dans JCB, un gestionnaire AJAX se compose de :

* **Contrôleur :** `/controllers/ajax.json.php`
* **Modèle :** `/models/ajax.php`

[00:10:04](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h10m04s)

Le contrôleur enregistre et exécute les tâches AJAX.
Le modèle définit les méthodes correspondantes telles que :

```php
public function createUser()
{
    // custom logic using expertdatabaseHelper::createUser()
}
```

[00:11:31](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h11m31s)

Ces méthodes :

* Récupérez les données du formulaire à l'aide du filtre d'entrée de Joomla.
* Valider et désinfecter les valeurs.
* Appelez la méthode Helper pour créer l'utilisateur.

JCB vous permet de définir ces tâches directement dans l'interface du générateur de composants sous **Méthodes Ajax**, en les mappant à vos fonctions PHP.

---

<a id="6-global-helper-integration"></a>
## 6. Intégration globale de l'assistance

[00:13:17](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h13m17s)

La classe Global Helper dans JCB fournit des fonctions réutilisables telles que `createUser()`, `addToGroup()` ou `getUserField()`.
Si vous améliorez l'une de ces fonctions, vous pouvez **créer le projet JCB sur GitHub** et soumettre une pull request.

[00:14:17](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h14m17s)

> **Remarque :** La méthode `createUser()` **n'ajoute pas** automatiquement les utilisateurs à un groupe d'utilisateurs Joomla.
> Vous devrez gérer cette logique dans votre composant ou via des hooks de post-création.

---

<a id="7-retrieving-and-displaying-user-data"></a>
## 7. Récupération et affichage des données utilisateur

[00:14:53](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h14m53s)

Lors du chargement de la page, une méthode `getUser` peut récupérer les données utilisateur à l'aide d'AJAX.
Le backend PHP récupère l'enregistrement utilisateur et le renvoie sous forme de réponse codée en JSON.

[00:15:51](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h15m51s)

En Javascript :

```javascript
$.ajax({
    url: 'index.php?option=com_expertdatabase&task=ajax.getUser&format=json',
    data: { user_id: selectedUserId },
    success: function(response) {
        // Populate the user data into the view
    }
});
```

Cela vous permet de charger, mettre à jour et afficher dynamiquement les informations utilisateur sans actualiser la page.

---

<a id="8-using-tokens-for-security"></a>
## 8. Utiliser des jetons pour la sécurité

[00:18:01](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h18m01s)

Incluez toujours un **jeton CSRF** dans chaque demande AJAX ou de formulaire pour empêcher les attaques de scripts intersites (XSS).

<a id="in-php"></a>
### En PHP :

```php
echo JHtml::_('form.token');
```

<a id="in-javascript-front-end-calls"></a>
### En JavaScript (appels front-end) :

```javascript
data[ '<?php echo JSession::getFormToken(); ?>' ] = 1;
```

[00:18:28](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h18m28s)

Les jetons sont automatiquement gérés dans la zone d'administration mais doivent être ajoutés manuellement sur le front-end.

---

<a id="9-extending-or-modifying-the-create-user-helper"></a>
## 9. Extension ou modification de l'assistant de création d'utilisateur

[00:20:20](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h20m20s)

Si vous devez modifier l'implémentation :

1. **Fork JCB** sur GitHub.
2. Localisez les **fichiers du compilateur** sous :

   ```
   administrator/components/com_componentbuilder/helpers/compiler/
   ```3. Recherchez la fonction `createUser`.
4. Modifiez sa logique pour l'adapter à vos besoins.

[00:21:38](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h21m38s)

Étant donné que ces méthodes d'assistance sont générées dynamiquement lors de la compilation, vous devez modifier la logique du compilateur plutôt que de modifier directement le code du composant compilé.

---

<a id="10-summary"></a>
## 10. Résumé

Intégration de la **méthode Create User Helper** dans JCB :

1. Activez l'assistant dans la zone **Composant > Bibliothèque et assistants**.
2. Utilisez `yourComponentHelper::createUser($new)` pour créer par programme des utilisateurs Joomla.
3. Pour une interaction dynamique, utilisez les **modèles AJAX** et les **contrôleurs**.
4. Incluez toujours des **jetons CSRF** pour des raisons de sécurité.
5. Étendez ou personnalisez via **Fichiers du compilateur** pour des modifications permanentes.

---

<a id="final-note"></a>
### Note finale

[00:19:41](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h19m41s)

Cette fonctionnalité démontre la puissance de Joomla Component Builder en tant qu'**outil de développement**, et pas seulement en tant que générateur d'interface utilisateur.
Il vous permet d'intégrer une logique de création d'utilisateurs dynamique et sécurisée directement dans vos composants.

---
