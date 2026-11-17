> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-a-custom-time-field"></a>
# Ajout d'un champ horaire personnalisé

*Utilisation du générateur de composants Joomla (JCB)*

<a id="video-reference"></a>
### Référence vidéo

[00:00:00](https://www.youtube.com/watch?v=epA9zv4yWu0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Cliquez sur ces liens horaires pour regarder le didacticiel YouTube.*)

---

<a id="1-overview"></a>
## 1. Aperçu

Dans Joomla Component Builder, un **champ d'heure personnalisé** vous permet de capturer des valeurs d'heure spécifiques (par exemple, `05:15`) dans vos composants. Étant donné que l'heure est stockée sous forme d'entier dans les bases de données, vous ne pouvez pas utiliser un format d'heure autonome : elle doit soit être stockée dans le cadre d'une date/heure, soit être validée via la saisie de texte.

Ce guide vous guide à travers :

* Création d'un **champ de texte** pour la saisie du temps
* Ajout d'une **règle de validation personnalisée (Form Rule)**
* Implémentation de la **validation côté serveur et JavaScript**
* Intégration de **champs temporels dans des structures répétables**

---

<a id="2-setting-up-a-time-field"></a>
## 2. Configuration d'un champ horaire

[00:00:21](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h00m21s)

Si vous souhaitez que les utilisateurs saisissent une heure telle que `05:15`, vous pouvez :

1. Créez un **champ de texte** dans JCB.
2. Validez-le à l'aide d'une **expression régulière (Regex)** pour garantir le bon format d'heure.

> **Conseil :** L'expression régulière peut être appliquée via une **règle de formulaire Joomla personnalisée**, garantissant une validation côté serveur au-delà de JavaScript.

---

<a id="3-creating-a-custom-form-rule"></a>
## 3. Création d'une règle de formulaire personnalisée

[00:01:23](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h01m23s)

Pour valider correctement le format de l'heure, vous allez créer une règle de formulaire Joomla personnalisée.

<a id="steps"></a>
### Étapes :

1. Accédez à votre dossier **Bibliothèques Joomla** :
   `libraries/src/Form/Rule/`

2. Examinez les règles existantes (par exemple, `EmailRule.php`, `UrlRule.php`) pour comprendre leur structure.
   [00:02:21](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h02m21s)

3. Créez un nouveau fichier, par exemple :
   `/libraries/src/Form/Rule/TimeRule.php`

4. Prolongez `Joomla\CMS\Form\FormRule` :

   ```php
   class JFormRuleTime extends FormRule
   {
       protected $regex = '^(?:[01]\d|2[0-3]):[0-5]\d$';
   }
   ```

   [00:02:43](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h02m43s)

5. Dans le **modèle XML de votre composant** (par exemple, `models/forms/item.xml`), ajoutez :

   ```xml
   <field name="event_time" type="text" label="Event Time" validate="time" filter="string" />
   ```

Cela connecte votre champ de formulaire à votre nouvelle règle de validation.

---

<a id="4-adding-the-field-in-component-builder"></a>
## 4. Ajout du champ dans le générateur de composants

[00:04:15](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h04m15s)

Dans **Component Builder** :

1. Accédez à **Champs → Nouveau**.
2. Choisissez **Type :** `text`.
3. Sous **Validation**, saisissez le nom de votre règle personnalisée (`time`).
4. Définissez **Filtre** sur `string`.

[00:04:44](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h04m44s)

Cette configuration garantit que les données sont filtrées et validées correctement sur le client et le serveur.

---

<a id="5-enhancing-with-javascript-validation"></a>
## 5. Amélioration avec la validation JavaScript

[00:05:00](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h05m00s)

Pour améliorer l'expérience utilisateur, vous pouvez ajouter une validation JavaScript au champ pour restreindre les caractères non valides.

Exemples d'étapes :

1. Ajoutez une **classe ou un identifiant unique** à votre champ.
2. Incluez JavaScript dans la **zone de script de pied de page de votre vue** (accessible dans la section View Scripts de JCB).
3. Le script ne doit autoriser que les chiffres et les deux-points (`:`).

[00:05:37](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h05m37s)

Vous pouvez utiliser l'ID du champ (par exemple, celui de l'inspecteur de votre navigateur) pour le cibler directement :

```js
document.getElementById('jform_event_time').addEventListener('input', function() {
  this.value = this.value.replace(/[^0-9:]/g, '');
});
```

Si des données non valides sont saisies, la saisie peut être effacée ou un message peut être affiché.

---

<a id="6-using-time-date-field-in-repeatable-fields"></a>
## 6. Utilisation du champ Heure-Date dans les champs répétables

[00:06:46](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h06m46s)

Lorsque vous travaillez avec des **champs répétables**, les champs de calendrier standard ne fonctionnent pas directement en raison de la façon dont les instances dynamiques sont gérées.
Pour surmonter ce problème, JCB inclut un **sélecteur DateTime personnalisé** intégré via JavaScript.

[00:08:08](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h08m08s)

<a id="key-steps"></a>
### Étapes clés :

1. Utilisez un **fichier JavaScript personnalisé** ajouté dans la section **Scripts** de JCB.
2. Parcourez chaque instance répétable à l'aide de JavaScript ou de PHP pour attacher le sélecteur de manière dynamique.
3. Exemple (simplifié) :

   ```js
   for (let i = 0; i < 50; i++) {
       let field = document.getElementById('time_field_' + i);
       if (field) {
           jQuery(field).datetimepicker({
               format: 'H:i',
               step: 15
           });
       }
   }
   ```

[00:09:52](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h09m52s)

---

<a id="7-handling-multiple-time-date-fields"></a>
## 7. Gestion de plusieurs champs heure-date

[00:10:51](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h10m51s)

Lorsque votre composant comprend plusieurs champs horaires (par exemple, heures de début, de fin ou cibles), JCB vous permet de les gérer efficacement en :

* Définition d'un éventail de types de champs ciblés.
* Utilisation d'une boucle PHP pour initialiser dynamiquement leurs sélecteurs date-heure, réduisant ainsi le code redondant.

[00:11:44](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h11m44s)

---

<a id="8-community-documentation-and-help-resources"></a>
## 8. Documentation communautaire et ressources d'aide

[00:12:14](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h12m14s)

Joomla Component Builder fournit des liens de documentation intégrés accessibles via le **menu Aide** dans chaque vue de liste.

Vous pouvez accéder au **Wiki** officiel et contribuer à l'amélioration de la documentation :

* **URL :** [Readme Documentation](http://projects.vdm.io/projects/Joomla-component-builder/wiki)

Si vous souhaitez contribuer ou demander de la documentation d'aide pour votre composant, contactez les responsables du projet.

[00:14:40](https://www.youtube.com/watch?v=epA9zv4yWu0&t=00h14m40s)

---

<a id="9-summary"></a>
## 9. Résumé

* Utilisez des **champs de texte** avec des **règles de formulaire** personnalisées pour la saisie de l'heure.
* Implémentez la **validation basée sur Regex** en PHP et la **restriction de caractères** en JavaScript.
* Pour les **champs répétables**, assurez une initialisation dynamique à l'aide de boucles JavaScript.
* Explorez **l'intégration de scripts de Component Builder** pour un contrôle total.
* Profitez du **JCB Wiki** pour apprendre et contribuer.

---
