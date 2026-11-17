> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="setup-site-edit-view-in-joomla-component-builder"></a>
# Configurer la vue de modification du site dans Joomla Component Builder

Découvrez comment configurer et activer la modification d'une **Vue administrateur** sur le **site frontal** à l'aide de Joomla Component Builder (JCB). Cela permet aux utilisateurs de **créer** et **modifier** des éléments de composant directement à partir de l'interface publique - avec des autorisations contrôlant qui peut faire quoi. Les vues de site frontend partagent désormais les mêmes blocs de construction modulaires mis en évidence dans la documentation : un Get dynamique principal alimente vos modèles, des Gets personnalisés en option alimentent des mises en page ou des bibliothèques supplémentaires et des espaces réservés de code personnalisé réutilisables gardent votre logique bien rangée.

---

<a id="1-add-admin-view-to-the-front-end-site"></a>
## 1. Ajouter une vue administrateur au site frontal

[00:00:00](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h00m00s)

JCB permet de relier une **Admin View** (l'interface d'édition backend) au **front-end** de votre site Web Joomla afin que les utilisateurs puissent modifier ou soumettre des données à partir du site.

1. **Compilez et installez** votre composant à l'aide du compilateur de JCB.
2. Ouvrez votre composant installé dans Joomla.
3. Dans cet exemple, le **Composant de démonstration** contient une vue d'administration appelée **"Looks"**.
4. Si vous ouvrez la *Vue en liste* pour « Looks », vous trouverez des champs tels que :

* Courriel
   * Téléphone portable
   * Date de naissance
   * Image
   * Site Web
   * Paramètres de publication, d'autorisations et de structure

Ces champs forment collectivement ce que JCB appelle une **Vue Admin** : une structure définissant la façon dont les enregistrements sont créés et modifiés dans votre composant.

---

<a id="2-add-editing-area-to-the-front-end"></a>
## 2. Ajouter une zone d'édition au front-end

[00:01:50](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h01m50s)

Pour rendre la vue administrateur modifiable à partir du front-end du site :

1. Accédez à l'**onglet Autorisations** dans la configuration de la vue de votre composant.
2. Vous verrez des contrôles pour :

* **Autorisations globales** (définies dans *Options*)
   * **Autorisations locales** (par vue)

Par exemple:

* Si les utilisateurs publics doivent pouvoir **soumettre de nouveaux éléments**, définissez **"Créer"** sur *Autoriser*.
* Pour leur permettre de **modifier leurs propres soumissions**, définissez également **"Modifier la propriété"** et **"Modifier l'état"** sur *Autoriser*.

> **Conseil :** Ces autorisations s'appliquent à la fois globalement et localement par vue. Assurez-vous que les deux sont configurés correctement si les modifications ne sont pas visibles sur le site.

---

<a id="3-understand-the-two-permission-switches"></a>
## 3. Comprendre les deux commutateurs d'autorisation

[00:03:30](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h03m30s)

Il existe **deux commutateurs d'autorisation principaux** qui déterminent l'accès frontal :

1. **Global Switch :** Situé sous *Options* - contrôle l'accès à l'ensemble du composant.
2. **Commutateur local :** Trouvé dans chaque vue d'administration - contrôle l'accès à cette vue spécifique.

Si un formulaire de modification frontale n'apparaît pas ou ne s'ouvre pas, revisitez ces paramètres pour vous assurer que le groupe d'utilisateurs approprié (par exemple, *Enregistré* ou *Auteur*) dispose des autorisations de modification.

---

<a id="4-enable-site-edit-view-in-component-settings"></a>
## 4. Activer la vue Modification du site dans les paramètres du composant

[00:04:21](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h04m21s)

Permettez maintenant à JCB de générer le code pour la vue Modification du site.

1. Ouvrez **JCB → Composants** et sélectionnez votre composant.

2. Dans l'onglet **Paramètres**, ouvrez la configuration qui répertorie toutes les vues d'administration liées.

3. Assurez-vous que **"Modifier/Créer une vue du site"** est défini sur **Oui**.

* Cela indique à JCB de générer automatiquement une **Vue du site**, un **Modèle** et un **Contrôleur** pour cette vue administrateur.
   * Le formulaire frontal sera alors disponible pour éditer ou créer des éléments.

4. Cliquez sur **Enregistrer**, puis sur **Enregistrer et fermer**.

5. Recompilez votre composant et réinstallez-le.

---

<a id="5-inspect-generated-code-mvc-structure"></a>
## 5. Inspecter le code généré : structure MVC

[00:06:05](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h06m05s)

Après compilation, vérifiez votre installation Joomla :

* Accédez à `/components/com_yourcomponent/`
* Vous trouverez :

  * `/controllers/look.php`
  * `/models/look.php`
  * `/views/look/`

Chacun correspond aux fichiers **Model-View-Controller** (MVC) créés par JCB.

Le code généré est similaire au backend mais adapté pour le front-end. Il comprend les scripts nécessaires, la gestion des formulaires et les ajustements de mise en page adaptés aux utilisateurs du site.

> **Remarque :** Bien que le code soit créé, JCB ne génère pas automatiquement de liens de menu ou de boutons pour accéder à ces formulaires frontaux. Ceux-ci doivent être ajoutés manuellement.

---

<a id="6-add-manual-links-to-the-front-end"></a>
## 6. Ajouter des liens manuels au front-end

[00:07:51](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h07m51s)

Pour permettre aux utilisateurs d'accéder et de modifier des éléments spécifiques du site :

1. Accédez à **JCB → Vues du site**.
2. Vous verrez :

* `Looks` (affichage liste)
   * `Looking` (éventuellement une vue associée)

Étant donné que la vue de modification du site « Look » a été générée automatiquement, vous n'avez pas besoin de la créer à nouveau. Cependant, vous devez créer manuellement des **liens** vers celui-ci.

3. Ouvrez les **GETs dynamiques** dans JCB.
4. Localisez les entrées d'requête dynamique pour « Looks » et « Looking ».
5. Modifiez l'requête dynamique « Looks » – dans sa zone **Script personnalisé**, recherchez le code qui ressemble à ceci :

   ```php
   if ($cando->get('core.edit')) {
       $item->edit_link = '<a href="' . JRoute::_('index.php?option=com_demo&view=look&id=' . (int) $item->id) . '">Edit</a>';
   }
   ```

Cet extrait ajoute dynamiquement un **bouton Modifier** pour les utilisateurs autorisés.
La méthode d'assistance `getAction()` détermine si l'utilisateur connecté peut modifier l'élément spécifique.

---

<a id="7-add-button-to-create-new-items"></a>
## 7. Ajouter un bouton pour créer de nouveaux éléments

[00:11:19](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h11m19s)

Pour permettre aux utilisateurs de créer de nouveaux éléments depuis le front-end :

1. Copiez le script du bouton d'édition utilisé dans Dynamic Get.

2. Modifiez le lien pour qu'il pointe vers **ID = 0** (nouvel élément) :

   ```php
   <a href="index.php?option=com_demo&view=look&id=0">Create New Look</a>
   ```

3. Placez ce bouton avant votre liste ou tableau d'éléments dans la vue du site.

Cela ajoute un bouton "Nouveau look" qui charge le formulaire de création front-end.

---

<a id="8-understand-the-helper-class-and-permissions-logic"></a>
## 8. Comprendre la classe d'assistance et la logique des autorisations

[00:12:23](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h12m23s)

JCB ajoute automatiquement un fichier d'assistance à votre composant, par exemple :

`/components/com_demo/helpers/demo.php`

Dans ce fichier, localisez la méthode :

```php
public static function getAction($itemId)
```

Cette méthode :

* Vérifie les autorisations des utilisateurs (`core.edit`, `core.edit.own`, `core.create`)
* Renvoie un objet contenant des valeurs booléennes indiquant ce que l'utilisateur peut faire
* Est utilisé par le script d'requête dynamique pour afficher ou masquer les liens de modification/création

> **Conseil :** Vous pouvez utiliser `var_dump($cando); exit;` pour déboguer et inspecter les actions disponibles pour l'utilisateur connecté.

---

<a id="9-verify-and-adjust-permission-behavior"></a>
## 9. Vérifier et ajuster le comportement des autorisations

[00:14:33](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h14m33s)

Si l'édition ou la création frontale ne fonctionne pas :

* Vérifiez le paramètre **Autoriser** pour votre vue du site (« Looks »).
* Assurez-vous que la **structure des autorisations** est correctement alignée avec la logique de votre composant.

Souviens-toi:

> JCB injecte automatiquement une structure d'autorisation complète dans chaque vue d'administrateur et de site qu'il génère. Vérifiez toujours les autorisations **Global** et **Local** avant de procéder au dépannage.

---

<a id="summary"></a>
### Résumé

En suivant ces étapes, vous obtenez :

* Activation d'une vue de modification du site pour une vue d'administration ("Look")
* Autorisé les utilisateurs à modifier et créer des enregistrements sur le front-end
* Accès contrôlé via le système d'autorisation intégré de JCB
* Ajout de liens manuels pour gérer les fonctionnalités "Modifier" et "Nouveau"
* Compris comment `getAction()` gère les autorisations de manière dynamique

---
