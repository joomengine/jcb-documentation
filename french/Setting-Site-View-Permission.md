> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="setting-site-view-permission-in-joomla-component-builder"></a>
# **Définition de l'autorisation d'affichage du site dans Joomla Component Builder**

> Vidéo : *Définition de l'autorisation d'affichage du site* [00:00:00](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h00m00s)
> *(Cliquez sur les horodatages pour afficher des parties spécifiques de la vidéo)*

---

<a id="1-overview"></a>
## **1. Aperçu**

[00:00:00](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h00m00s)

Dans Joomla Component Builder (JCB), les **Autorisations d'affichage du site** contrôlent l'accès frontal pour chaque vue de votre composant. Utilisez-les pour déterminer qui peut afficher, créer, modifier ou supprimer des données du côté public de votre extension.
Par défaut, ces autorisations sont définies sur **"Non autorisé"**, car JCB s'appuie sur les **Autorisations globales des composants** de Joomla. À moins que ceux-ci ne soient explicitement écrits dans la base de données (soit manuellement, soit via un script), aucune vue du site ne sera accessible sur le front-end.

---

<a id="2-example-using-the-sermon-distributor-demo"></a>
## **2. Exemple : Utilisation de la démo Sermon Distributor**

[00:00:49](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h00m49s)

Ce didacticiel utilise le composant de démonstration **Sermon Distributor** (disponible comme exemple JCB).
Dans ce composant :

* Accédez à **Options → Autorisations**.
* Recherchez des termes tels que **"Site"** pour localiser les autorisations associées.

Vous trouverez des entrées telles que :

* `categories site access` (pluriel)
* `category site access` (singulier)
* `preachers`, `series`, `sermons`, etc.

Chacun de ces éléments détermine si une vue spécifique est accessible au public.
Par défaut, leurs valeurs sont **"Héritage"**, qui s'affiche comme **"Non autorisé"**, sauf si elles sont définies globalement.

> **Conseil :** Ce comportement par défaut empêche tout accès frontal non autorisé jusqu'à ce qu'une autorisation explicite soit accordée.

---

<a id="3-defining-a-default-site-view"></a>
## **3. Définir une vue de site par défaut**

[00:02:02](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h02m02s)

Pour améliorer l'expérience utilisateur lorsque des problèmes d'autorisation surviennent, JCB fournit un mécanisme **Default View**.

<a id="steps-to-configure-a-default-view"></a>
### **Étapes pour configurer une vue par défaut**

1. Ouvrez **Component Builder → Composants → [Votre composant] → Paramètres → Vues du site.**
2. Ajoutez ou modifiez une vue.
3. Cochez la case **Vue par défaut**.

[00:02:40](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h02m40s)

La **Vue par défaut** fait office de page de secours lorsque les utilisateurs tentent d'accéder à une page restreinte.
Il doit généralement s'agir d'une **page sans restriction** qui explique comment les utilisateurs peuvent y accéder (par exemple, en se connectant ou en mettant à niveau les autorisations).

[00:03:12](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h03m12s)

* Une seule **une** vue par défaut peut exister.
* Si plusieurs sont marqués, JCB utilisera le **premier** rencontré lors de la compilation.

[00:03:52](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h03m52s)

Lorsqu'une page restreinte est accessible, JCB **redirige** automatiquement l'utilisateur vers cette vue par défaut, évitant ainsi les boucles sans fin ou les erreurs 403.

> **Remarque :**
> Cette fonctionnalité évite les erreurs d'accès mais ne remplace pas la logique d'autorisation de Joomla : il s'agit d'un mécanisme de secours gracieux.

---

<a id="4-adding-custom-post-installation-scripts"></a>
## **4. Ajout de scripts de post-installation personnalisés**

[00:04:48](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h04m48s)

Vous pouvez automatiquement guider les administrateurs pour qu'ils définissent correctement les autorisations à l'aide de **scripts de post-installation PHP personnalisés**.

<a id="example-add-a-post-flight-message"></a>
### **Exemple : Ajouter un message après le vol**

Dans la section **PHP (Post-Flight)** du *Script d'installation* de votre composant :

```php
$app = \Joomla\CMS\Factory::getApplication();
$app->enqueueMessage(
    'First set the component global settings and permissions in the Options area. 
    The front end will not work as expected until each Site View has the correct access permissions.'
);
```

[00:05:54](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h05m54s)

Vous pouvez également :

* Transformez le message en un **lien** redirigeant vers la page Options.
* Ajoutez une logique pour **mettre à jour automatiquement les autorisations** après l'installation.

> **Option avancée :**
> Utilisez ici des scripts pour prédéfinir l'accès public aux vues du site si votre composant nécessite une disponibilité frontale immédiate.

---

<a id="5-understanding-site-root-behavior-in-code"></a>
## **5. Comprendre le comportement de la racine du site dans le code**

[00:06:38](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h06m38s)

Dans le code du composant généré, JCB vérifie les autorisations d'affichage du site à l'aide du **fichier d'accès** (par exemple, `access.xml`).

Lors de l'accès à une vue restreinte :

1. JCB vérifie si l'utilisateur a l'autorisation.
2. Sinon, il **redirige** l'utilisateur vers la **vue par défaut**.
3. Si la vue par défaut n'est pas accessible (pas la racine du site), JCB redirige vers la **page d'accueil du site**.

[00:07:32](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h07m32s)

Cela garantit que les conflits d'autorisations frontaux ne planteront jamais ou ne feront jamais de boucle sur le site.

> **Exemple :**
> Accès refusé sur la vue `/category` → Redirige vers `/preachers` (par défaut) → Si `/preachers` n'est pas accessible → Redirige vers la page d'accueil.

---

<a id="6-example-of-permission-error-handling"></a>
## **6. Exemple de gestion des erreurs d'autorisation**

[00:08:57](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h08m57s)

Si un utilisateur n'a pas l'autorisation, JCB affichera une erreur localisée, telle que :

```
COM_SERMONDISTRIBUTOR_NOT_AUTHORISED_TO_VIEW_CATEGORIES
```

Vous pouvez personnaliser ce message ou même ajouter une logique pour afficher une invite (par exemple, *"Veuillez vous connecter ou acheter un accès pour afficher cette section."*).

> **Idée d'amélioration :**
> Ajoutez un champ dans votre composant qui permet aux utilisateurs administrateurs de définir un **message personnalisé** pour un accès non autorisé.

---

<a id="7-using-custom-code-implementations"></a>
## **7. Utilisation d'implémentations de code personnalisé**

[00:09:35](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h09m35s)

JCB prend en charge les **implémentations de code personnalisé**, vous permettant de remplacer le code généré au moment de la compilation.

Utilisez-le pour :

* Insérez une logique d'accès personnalisée.
* Modifier le comportement de redirection.
* Modifier les messages liés aux autorisations.

[00:10:10](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h10m10s)

Pour des exemples de personnalisation plus détaillés, consultez le didacticiel dédié de JCB sur **Implémentation de code personnalisé**.

---

<a id="8-summary"></a>
## **8. Résumé**

| Fonctionnalité | Descriptif |
| ----------------------- | -------------------------------------------- |
| **Autorisation par défaut** | "Non autorisé" sauf accord explicite |
| **Vue par défaut** | Redirection de secours en cas d'accès non autorisé |
| **Script de post-installation** | Affiche les rappels de configuration ou l'accès aux paramètres automatiques |
| **Contrôle au niveau du code** | Redirection vers des vues sécurisées ou une page d'accueil |
| **Code personnalisé** | Modifier ou étendre la logique de contrôle d'accès |

---

<a id="best-practices"></a>
## **Bonnes pratiques**

* Définissez toujours une **Vue par défaut** pour éviter les boucles de redirection.
* Utilisez des **scripts post-vol personnalisés** pour rappeler ou appliquer les paramètres d'autorisation.
* Personnalisez les messages d'erreur pour une meilleure UX.
* Utilisez **Implémentations de code personnalisé** pour une logique d'accès complexe.
* Testez le comportement frontal de votre composant compilé après l'installation.

---
