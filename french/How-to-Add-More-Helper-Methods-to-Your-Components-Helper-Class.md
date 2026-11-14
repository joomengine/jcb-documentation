> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-add-more-helper-methods-to-your-components-helper-class"></a>
# Comment ajouter plus de méthodes d'assistance à la classe d'assistance de votre composant

Découvrez comment ajouter et gérer des méthodes d'assistance dans votre classe d'assistance de composant Joomla Component Builder (JCB) - à la fois pour les zones **admin** et **site**. Ce guide explique également comment inclure des classes d'assistance personnalisées et les déclencher globalement à l'aide du système d'événements de JCB.

---

<a id="overview"></a>
## Aperçu

Les classes d'assistance dans Joomla Component Builder vous permettent de stocker des méthodes PHP réutilisables accessibles dans tout votre composant - dans les contextes **admin** et **frontend (site)**.
Ce didacticiel montre comment :

* Ajoutez des méthodes d'assistance directement dans JCB.
* Faites la différence entre les fonctions d'assistance d'administration, de site et partagées (« les deux »).
* Appelez les méthodes d'assistance dans le code de votre composant.
* Incluez et enregistrez des fichiers d'assistance personnalisés.
* Utilisez des **événements globaux** pour déclencher automatiquement la logique d'assistance.

---

<a id="1-accessing-the-helper-class-interface"></a>
## 1. Accéder à l'interface de classe d'assistance

**Horodatage :** [00:00:14](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h00m14s)

1. Ouvrez votre **composant** dans Joomla Component Builder.
2. Accédez à l'onglet **"Libs & Helpers"**.

* Vous trouverez ici plusieurs domaines cibles pour les méthodes d'assistance :

* **Site Helper** - logique frontale uniquement.
     * **Admin Helper** - logique backend uniquement.
     * **Les deux** - méthodes partagées disponibles à la fois pour le frontend et le backend.

> **Conseil :** Utilisez « Les deux » lorsque vous souhaitez que la même aide soit disponible partout. C'est idéal pour les utilitaires à usage général (par exemple, formatage des dates, validation).

---

<a id="2-adding-helper-methods"></a>
## 2. Ajout de méthodes d'assistance

**Horodatage :** [00:00:44 - 00:01:43](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h00m44s)

Pour ajouter une nouvelle méthode d'assistance :

1. Dans la section **Site Helper**, cliquez sur **Ajouter une méthode**.
   Exemple:

   ```php
   public static function fancyDate($date)
   {
       // Example site-only method
       return date('F j, Y', strtotime($date));
   }
   ```

Cela crée une méthode appelée `fancyDate` disponible uniquement pour le **frontend**.

2. Dans **Admin Helper**, vous pouvez ajouter quelque chose comme :

   ```php
   public static function showAdminMessage()
   {
       return 'This is admin only';
   }
   ```

3. Dans la section **Les deux** :

   ```php
   public static function sharedMethod()
   {
       return 'This method is available in both admin and site areas.';
   }
   ```

> **Compilez votre composant** après avoir ajouté les méthodes d'assistance pour vous assurer qu'elles sont écrites dans les fichiers de classe d'assistance générés.

---

<a id="3-verifying-generated-helper-methods"></a>
## 3. Vérification des méthodes d'assistance générées

**Horodatage :** [00:02:10 - 00:03:01](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h02m10s)

Une fois que vous avez compilé et installé le composant :

* Dans la **zone d'administration** :
  Accédez à
  `administrator/components/com_demo/helpers/demo.php`
  Vous verrez vos fonctions `showAdminMessage()` et `sharedMethod()` à l'intérieur.

* Dans la **zone frontend (site)** :
  Aller à
  `components/com_demo/helpers/demo.php`
  Vous trouverez les fonctions `fancyDate()` et `sharedMethod()`.

> Les méthodes sous **"Les deux"** apparaissent dans **les deux fichiers d'assistance**, garantissant une logique partagée entre les environnements d'administration et de site.

---

<a id="4-calling-helper-methods-in-your-code"></a>
## 4. Appel de méthodes d'assistance dans votre code

**Horodatage :** [00:03:40 - 00:04:28](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h03m40s)

Les méthodes d'assistance peuvent être appelées à l'aide de la classe d'assistance enregistrée de Joomla.

Exemple : appel de la méthode `fancyDate()` dans la vue de votre site :

```php
use Joomla\CMS\Factory;

// Call helper method
$dateFormatted = DemoHelper::fancyDate($item->created);
```

Cet exemple formate une valeur de date à l'aide de la méthode `fancyDate()` définie précédemment.

> Les classes d'assistance sont automatiquement enregistrées par JCB lors de la génération des composants - aucune inclusion manuelle n'est nécessaire pour ces assistants intégrés.

---

<a id="5-adding-a-custom-helper-class-file"></a>
## 5. Ajout d'un fichier de classe d'assistance personnalisé

**Horodatage :** [00:05:06 - 00:06:01](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h05m06s)

Si vous préférez ajouter un **fichier d'assistance entièrement nouveau** (non géré par JCB) :

1. Utilisez le système **File and Folder Inclusion** de JCB.

* Vous pouvez choisir l'inclusion **de base** ou **avancée** en fonction de l'emplacement du fichier.
   * Définissez le chemin correct par rapport à la sortie ZIP.

2. Ajoutez votre fichier d'assistance PHP manuellement.
   Exemple :
   `administrator/components/com_demo/helpers/own.php`

3. À l’intérieur, définissez votre classe d’assistance :

   ```php
   class OwnHelper
   {
       public static function doSomething()
       {
           return 'Custom helper logic here.';
       }
   }
   ```

---

<a id="6-using-global-events-to-load-helpers-automatically"></a>
## 6. Utiliser les événements globaux pour charger automatiquement les assistants

**Horodatage :** [00:06:01 - 00:09:26](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h06m01s)

Vous pouvez déclencher automatiquement des événements chaque fois qu'une classe d'assistance est chargée à l'aide de **Global Events** dans JCB.

<a id="steps"></a>
### Étapes :

1. Dans les paramètres de votre composant JCB, ouvrez **Composant → Helper → Global Event (Admin)**.
   Ajoutez un extrait comme :

   ```php
   $this->triggerEvent('onDemoAdminHelperLoad', array('document' => $document));
   ```

Cela s'exécute à chaque fois que **l'assistant d'administration** est chargé.

2. Après la compilation, vérifiez votre fichier d'assistance généré :

* L'événement global apparaîtra sous forme d'extrait dans la classe d'assistance à l'administration.
   * L'objet document (`$document`) est transmis, vous permettant de manipuler la sortie de page ou les scripts globalement.

3. Pour enregistrer votre **classe d'assistance personnalisée**, prolongez l'événement :

   ```php
   require_once JPATH_COMPONENT_ADMINISTRATOR . '/helpers/own.php';
   $this->triggerEvent('onDemoAdminHelperLoad', array(new OwnHelper));
   ```

Désormais, vos méthodes d'assistance personnalisées sont disponibles automatiquement à chaque chargement de la classe d'assistance.

---

<a id="7-extending-to-the-site-frontend"></a>
## 7. Extension au site (Frontend)

**Horodatage :** [00:09:57 - 00:10:32](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h09m57s)

Vous pouvez reproduire le même processus pour l'**assistant de site** :

1. Utilisez **Événement global (site)** dans JCB.
2. Déplacez votre fichier d'assistance personnalisé vers le dossier d'assistance frontale :
   `components/com_demo/helpers/own.php`
3. Incluez-le avec :

   ```php
   require_once JPATH_COMPONENT_SITE . '/helpers/own.php';
   ```

Désormais, votre fichier d'assistance frontend se chargera également automatiquement à chaque fois que le composant s'exécutera.

---

<a id="8-when-to-use-global-events"></a>
## 8. Quand utiliser les événements globaux

**Horodatage :** [00:11:02 - 00:11:33](https://www.youtube.com/watch?v=VpSXsxZuhmM&t=00h11m02s)

Les événements mondiaux sont les mieux adaptés pour :

* Modification de l'**Objet Document** de Joomla avant le chargement d'une page.
* Y compris des scripts supplémentaires ou CSS de manière dynamique.
* Exécution du code de configuration sur toutes les vues.

Cependant, pour les méthodes d'assistance simples, il est généralement préférable de les ajouter directement à la classe d'assistance principale (admin/site/both) au lieu d'utiliser un fichier externe et un événement global.

> **Meilleure pratique :**
> Gardez la logique d'assistance centralisée dans le propre fichier d'assistance du composant, sauf s'il existe une bonne raison de modulariser avec des événements globaux.

---

<a id="summary"></a>
## Résumé

| Tâche | Localisation chez JCB | Objectif |
| ---------------------- | -------------------------------- | ---------------------------------- |
| Ajouter des méthodes d'assistance | Libs & Helpers → Admin/Site/Les deux | Définir des fonctions PHP réutilisables |
| Méthodes d'assistance d'appel | Dans les vues/modèles | Exécuter la logique à partir de la classe d'assistance |
| Ajouter un fichier d'assistance personnalisé | Inclusion de fichiers et de dossiers | Inclure des classes d'assistance autonomes |
| Utiliser les événements mondiaux | Composant → Assistant | Déclencher automatiquement la logique d'assistance |

---

<a id="final-notes"></a>
## Notes finales

L'ajout de méthodes d'assistance est une technique fondamentale dans le développement de Joomla Component Builder. Il vous permet de centraliser les fonctionnalités, de réutiliser efficacement la logique et de maintenir un code de composant plus propre.

Expérimentez avec les zones d'assistance intégrées et les événements globaux pour déterminer la structure la mieux adaptée à votre projet.

---
