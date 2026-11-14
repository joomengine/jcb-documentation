> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-filter-a-list-field-based-on-association-with-another-field"></a>
# Comment filtrer un champ de liste en fonction de l'association avec un autre champ

<a id="overview"></a>
## Aperçu

Dans de nombreux composants Joomla, vous devrez peut-être **filtrer les options d'un champ de liste en fonction de la valeur d'un autre champ**.
Un cas d'utilisation courant consiste à limiter la liste **Région** pour afficher uniquement les régions appartenant à un **Pays** sélectionné.

Ce guide montre comment y parvenir de manière dynamique dans **Joomla Component Builder (JCB)** en utilisant une combinaison de :

* JavaScript
* Ajax (Modèle + Contrôleur)
* PHP dans le back-end

Vous apprendrez à connecter deux champs liés, à récupérer des données via Ajax et à mettre à jour dynamiquement les listes déroulantes sans recharger les pages.

---

<a id="1-understanding-the-filtering-goal"></a>
## 1. Comprendre l'objectif de filtrage

**Horodatage :** [00:00:00](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h00m00s)

L'objectif est de **limiter un champ déroulant (liste)** en fonction de la valeur d'un autre champ - par exemple :

* Lors de la sélection d'un **Pays**, seules les **Régions** correspondantes sont chargées.
* Lorsqu'un pays est **non sélectionné**, le champ Région doit également être réinitialisé.

Cela améliore la convivialité et garantit la cohérence des données.

---

<a id="2-example-scenario-country-and-region-in-job-tracking-component"></a>
## 2. Exemple de scénario : Pays et région dans le composant "Suivi des tâches"

**Horodatage :** [00:00:43](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h00m43s)

Exemple de configuration :

* Composant : **Suivi des tâches**
* Vues d'administration : `Country` et `Region`
* Vue client : utilise les deux champs dans un formulaire associé.

Lors de la création ou de la modification d'un client :

* La sélection d'un pays charge uniquement ses régions associées.
* Si un pays n'a pas de régions, une option « Créer une région » apparaît.
* Si le pays possède des régions, il affiche « Sélectionner une région ».

---

<a id="3-javascript-implementation"></a>
## 3. Implémentation JavaScript

**Horodatage :** [00:04:30](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h04m30s)

Pour activer les mises à jour dynamiques des listes déroulantes, ajoutez du JavaScript personnalisé qui gère :

1. Stockage des données de toutes les régions
2. Demandes Ajax pour récupérer les régions filtrées
3. Mises à jour de l'interface utilisateur sur la sélection du pays

<a id="31-define-the-variables"></a>
### 3.1. Définir les variables

```javascript
var regions = {}; // Object storing all available regions
var region = '';  // Holds the currently selected region (if any)
```

Lorsque la page se charge, toutes les régions sont analysées dans la variable `regions`.
Plus tard, seuls ceux appartenant au pays sélectionné seront réinsérés dans la liste déroulante.

---

<a id="32-show-the-loading-indicator"></a>
### 3.2. Afficher l'indicateur de chargement

**Horodatage :** [00:06:23](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h06m23s)

Pour améliorer l'UX, affichez un chargeur pendant que la liste déroulante se met à jour :

```javascript
jQuery("#loading").show();
```

Cette classe peut utiliser le spinner intégré de Joomla ou votre chargeur personnalisé.

Ensuite, effacez les options existantes de la liste Région avant de la repeupler :

```javascript
regionField.find('option').remove();
regionField.trigger('liszt:updated');
```

> **Remarque :** `liszt:updated` est un ancien déclencheur de plug-in Chosen utilisé par les champs de liste Joomla.
> Les versions futures pourront utiliser `chosen:updated`.

---

<a id="33-fetch-filtered-regions-with-ajax"></a>
### 3.3. Récupérer les régions filtrées avec Ajax

**Horodatage :** [00:07:51](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h07m51s)

Définissez la fonction `getRegion()` pour envoyer la requête Ajax :

```javascript
function getRegion(countryId) {
  if (!countryId) return;

  jQuery.ajax({
    type: "POST",
    url: "index.php?option=com_jobtracking&task=getRegion",
    data: { country: countryId },
    success: function(result) {
      setRegion(result);
    }
  });
}
```

Une fois la réponse reçue, il appelle `setRegion()` pour mettre à jour la liste déroulante.

---

<a id="34-updating-the-region-dropdown"></a>
### 3.4. Mise à jour de la liste déroulante des régions

**Horodatage :** [00:09:38](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h09m38s)

La fonction `setRegion()` remplit le champ Région :

```javascript
function setRegion(data) {
  jQuery.each(data, function(i, id) {
    if (regions[id]) {
      regionField.append('<option value="' + id + '">' + regions[id] + '</option>');
    }
  });
  regionField.trigger('liszt:updated');
}
```

S'il n'existe aucune région pour un pays :

* Afficher "Créer une région"
* En option, ouvrez le modal pour en créer un

```javascript
var select_a_region = "Select a Region";
var create_a_region = "Create a Region";
```

---

<a id="35-handle-button-functionality"></a>
### 3.5. Fonctionnalité des boutons de la poignée

**Horodatage :** [00:12:22](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h12m22s)

Si votre champ de liste comprend un bouton « Créer » ou « Modifier » :

* Assurez-vous que le nom de la fonction JS suit la convention de dénomination de JCB :
  `regionButton()` si le nom de votre champ est `region`.
* Exécutez une routine de correction si nécessaire après avoir repeuplé la liste.

---

<a id="36-detect-field-changes"></a>
### 3.6. Détecter les modifications de champ

**Horodatage :** [00:14:06](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h14m06s)

Mettez automatiquement à jour la liste des régions chaque fois que le pays change :

```javascript
adminForm.on('change', '#jform_country', function() {
  var countryId = jQuery(this).val();
  getRegion(countryId);
});
```

Cela garantit que `getRegion()` s’exécute à la fois lors du chargement de la page et du changement de champ.

---

<a id="4-php-backend-ajax-model-and-controller"></a>
## 4. Backend PHP : modèle et contrôleur Ajax

**Horodatage :** [00:15:13](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h15m13s)

Dans JCB, les requêtes Ajax sont traitées via un **modèle Ajax centralisé** et un **contrôleur**.

<a id="41-ajax-controller"></a>
### 4.1. Contrôleur Ajax

Définit l'entrée acceptée et la tâche :

```php
$input = $this->input->get('country', 0, 'INT');
$this->task = 'getRegion';
```

<a id="42-ajax-model-method"></a>
### 4.2. Méthode du modèle Ajax

Dans le modèle Ajax (`models/ajax.php`) :

```php
public function getRegion() {
    $countryId = (int) $this->input->get('country', 0);
    $db = Factory::getDbo();
    $query = $db->getQuery(true)
        ->select($db->quoteName('id'))
        ->from($db->quoteName('#__regions'))
        ->where($db->quoteName('published') . ' = 1')
        ->where($db->quoteName('country') . ' = ' . $db->quote($countryId));
    $db->setQuery($query);
    return $db->loadColumn() ?: false;
}
```

Cela renvoie un tableau d'ID de région liés au pays sélectionné.

> **Conseil :** Ajustez les noms des tables et des colonnes en fonction de votre propre composant.

---

<a id="5-custom-field-setup-in-jcb"></a>
## 5. Configuration des champs personnalisés dans JCB

**Horodatage :** [00:18:34](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h18m34s)

Les champs **Pays** et **Région** sont des **Champs de liste personnalisés** créés dans JCB.

<a id="field-region"></a>
### Champ : Région

* **Type :** Liste
* **Bouton :** `True` (pour autoriser l'option "Créer")
* **Tableau source :** Régions
* **Étiquette dynamique :** Peut utiliser PHP dans la définition XML pour l'étiquette ou la description du champ

Vous pouvez ajouter du PHP en ligne dans le XML ou dans la zone "Type PHP" de la définition du champ.

> **Meilleure pratique :**
> Conserver l'essentiel de la logique dans la vue Admin (JavaScript + Ajax),
> et utilisez le champ personnalisé XML uniquement pour définir la structure et les relations.

---

<a id="6-final-result"></a>
## 6. Résultat final

**Horodatage :** [00:20:15](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h20m15s)

Lorsqu’il est correctement mis en œuvre :

* La sélection d'un pays filtre dynamiquement la liste déroulante des régions.
* Ajax garantit des mises à jour transparentes.
* Le même modèle peut être appliqué à **tous les champs associés** - par exemple, Catégories → Sous-catégories, Marque → Modèles, etc.

---

<a id="7-summary"></a>
## 7. Résumé

| Étape | Descriptif |
| ------ | ----------------------------------------------------------- |
| **1.** | Créez deux champs de liste personnalisés associés (Pays et Région) |
| **2.** | Ajouter la méthode Ajax (`getRegion`) au modèle et au contrôleur |
| **3.** | Écrivez des fonctions JS (`getRegion`, `setRegion`) dans la vue administrateur |
| **4.** | Attacher un écouteur JS pour les modifications du champ Pays |
| **5.** | Gérer éventuellement le comportement du bouton « Créer une région » |
| **6.** | Compilez et installez votre composant |

---

<a id="helpful-tips"></a>
## Conseils utiles

* Désinfectez toujours les entrées et validez les données renvoyées.
* Utilisez un nom cohérent pour les champs (par exemple, `country`, `region`) pour éviter toute confusion.
* JCB compile toutes les méthodes Ajax dans un seul fichier (`models/ajax.php`) – pas besoin d'ajouter manuellement plusieurs contrôleurs.
* Si vous ciblez la table d'un autre composant, assurez-vous de connaître le nom du champ d'association.

---
