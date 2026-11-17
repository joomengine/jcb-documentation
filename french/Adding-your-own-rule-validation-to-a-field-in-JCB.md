> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="adding-your-own-rule-validation-to-a-field-in-joomla-component-builder-jcb"></a>
# Ajout de votre propre validation de règle à un champ dans Joomla Component Builder (JCB)

<a id="overview"></a>
## Aperçu

Les règles de validation garantissent que les valeurs des champs remplissent certaines conditions **avant d'être enregistrées** dans la base de données. JCB prend en charge le système de validation intégré de Joomla et permet aux développeurs d'ajouter des **règles personnalisées** à l'aide des classes JFormRule.

Dans ce guide, nous allons :

* Ajoutez une propriété de validation personnalisée à un type de champ.
* Créez un fichier de règles de validation personnalisé (`strlenTen`).
* Intégrez la règle dans le composant Hello World.
* Testez la règle et affichez des messages de validation personnalisés.

---

<a id="1-open-the-admin-view-and-locate-the-target-field"></a>
## 1. Ouvrez la vue administrateur et localisez le champ cible

[00:00:32](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m32s)

1. Ouvrez **Joomla Component Builder (JCB)** et sélectionnez votre composant **Hello World**.
2. Accédez à l'onglet **Vues d'administration** et ouvrez la vue **Salutations**.
3. Localisez le champ **Salutations** (généralement de type `Textarea`).
4. Vérifiez les attributs du champ - si l'option `validation` est manquante, elle peut être ajoutée manuellement dans la configuration Fieldtype.

> *Astuce : Si votre version JCB ne dispose pas de la propriété "validation", vous pouvez modifier directement le type de champ pour l'ajouter.*

---

<a id="2-add-the-validation-attribute-to-a-field-type"></a>
## 2. Ajouter l'attribut de validation à un type de champ

[00:01:55](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m55s)

1. Dans JCB, accédez à **Fieldtypes** dans la vue Admin.
2. Sélectionnez un **Fieldtype** à modifier (par exemple, `Textarea`).
3. Ajoutez un nouvel attribut :

* **Nom :** `validate`
   * **Réglable :** Oui
   * **Obligatoire :** Non
   * **Traductible :** Non
   * **Description :** *(Une règle pour valider ce champ avant de sauvegarder.)*
4. Enregistrez et fermez.

Désormais, lorsque vous modifiez un champ à l'aide de ce type de champ, vous verrez une option **Valider** disponible.

---

<a id="3-set-a-custom-validation-rule"></a>
## 3. Définir une règle de validation personnalisée

[00:03:03](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m03s)

1. Revenez à votre **Vue Administrateur → Salutations**.

2. Modifiez le champ `Greeting`.

3. Dans la propriété **Validate**, saisissez le nom de votre règle personnalisée. Par exemple :

   ```xml
   validate="strlenTen"
   ```

4. Enregistrez et fermez.

> JCB prend en charge les règles de validation intégrées de Joomla (comme `email`, `url`, etc.), mais des règles personnalisées peuvent être définies comme des **règles de formulaire** en ajoutant votre propre classe PHP.

---

<a id="4-create-a-custom-validation-rule-file"></a>
## 4. Créez un fichier de règles de validation personnalisé

[00:04:14](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m14s)

1. Dans votre installation JCB locale, ouvrez le dossier **Custom** :

   ```
   administrator/components/com_componentbuilder/custom/
   ```

2. Créez un nouveau fichier PHP nommé `strlenTen.php`.

3. Ajoutez le code de règle suivant (issu du didacticiel) :

   ```php
   <?php
   defined('_JEXEC') or die('Restricted access');

   class JFormRuleStrlenTen extends JFormRule
   {
       public function test(&$element, $value, $group = null, &$input = null, &$form = null)
       {
           return strlen($value) > 10;
       }
   }
   ```

4. Enregistrez le fichier.
   Ce fichier définit une règle simple qui vérifie si la chaîne d'entrée contient **plus de 10 caractères**.

---

<a id="5-register-the-rule-in-jcbs-custom-files"></a>
## 5. Enregistrez la règle dans les fichiers personnalisés de JCB

[00:06:03](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m03s)

1. Dans JCB, ouvrez à nouveau votre composant **Hello World**.
2. Accédez à **Paramètres → Ajouter des fichiers et dossiers personnalisés**.
3. Cliquez sur **Créer des fichiers et dossiers de composants pour ce composant Joomla**.
4. Localisez votre fichier personnalisé (`strlenTen.php`) dans la liste.
5. Définissez son **Chemin cible** sur :

   ```
   admin/models/rules/
   ```6. Activez **Mettre à jour ce fichier** = **Oui**.
7. Enregistrez et fermez.

> JCB gère automatiquement le placement des fichiers lors de la compilation, en utilisant le chemin `admin/models/rules` pour les fichiers de règles.

---

<a id="6-add-license-and-component-tags"></a>
## 6. Ajouter des balises de licence et de composants

[00:07:34](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m34s)

Ajoutez ces espaces réservés à votre fichier de règles pour une personnalisation automatique lors de la compilation :

```php
###BOM###
/**
 * @license ###LICENSE###
 * @package ###component###
 */
```

* `###BOM###` - garantit le format d'en-tête de fichier correct.
* `###component###` - remplacé par le nom réel du composant.
* `###LICENSE###` - remplacé par le texte de licence de votre composant.

---

<a id="7-compile-and-test-the-rule"></a>
## 7. Compiler et tester la règle

[00:08:54](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m54s)

1. Accédez au **Compilateur** dans JCB et compilez votre composant.
2. Installez le package généré dans Joomla.
3. Accédez à :

   ```
   administrator/components/com_hello_world/models/rules/
   ```

Vous devriez maintenant voir votre fichier `strlenten.php` (automatiquement en minuscules).
4. Ouvrez le fichier - notez que votre en-tête de licence et vos balises de composants ont été appliquées.

<a id="test-in-the-admin-view"></a>
### Testez dans la vue Administrateur :

* Accédez à **Composants → Hello World → Salutations → Nouveau**.
* Entrez une chaîne courte (moins de 10 caractères).
* Cliquez sur ** Enregistrer **. Vous verrez :
  `Warning: Invalid Field: Greetings`

Si cela ne se déclenche pas :

* Assurez-vous que le nom de validation et le nom de fichier sont **tous en minuscules** (`strlenten`).

---

<a id="8-add-a-custom-validation-message"></a>
## 8. Ajouter un message de validation personnalisé

[00:12:33](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m33s)

Vous pouvez afficher un message d'erreur personnalisé au lieu du message par défaut de Joomla.

<a id="option-a---add-message-inside-php-rule"></a>
### Option A - Ajouter un message dans la règle PHP :

Modifier `strlenten.php` :

```php
$element->addAttribute('message', 'Field must have more than 10 characters!');
return false;
```

<a id="option-b---add-message-in-xml-field-definition"></a>
### Option B - Ajouter un message dans la définition du champ XML :

[00:13:45](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m45s)

1. Dans JCB, accédez à **Fieldtypes** → `Textarea`.
2. Ajoutez un nouvel attribut :

* **Nom :** `message`
   * **Modifiable :** Oui
   * **Traductible :** Oui
   * **Facultatif :** Oui
   * **Description :** *(Affiché lorsque la validation échoue.)*
3. Enregistrez et fermez.
4. Dans votre champ XML **Salutations**, ajoutez :

   ```xml
   message="COM_HELLO_WORLD_GREETING_GREETING_MESSAGE"
   ```5. Compilez et réinstallez votre composant.

> La méthode XML est préférable lorsque vous n'avez besoin que d'un seul message d'erreur traduit.

---

<a id="9-verify-the-final-behavior"></a>
## 9. Vérifiez le comportement final

[00:15:00](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m00s)

1. Ouvrez **Salutations → Nouveau** dans l'administrateur Joomla.
2. Saisissez une courte chaîne et enregistrez. Vous devriez voir votre message personnalisé :

   ```
   Warning: Field must have more than 10 characters!
   ```3. Entrez une chaîne valide (> 10 caractères) et enregistrez - l'enregistrement est enregistré avec succès.

---

<a id="10-summary"></a>
## 10. Résumé

[00:16:56](https://www.youtube.com/watch?v=Z6-ggKtX35o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m56s)

Vous avez réussi :

* Ajout d'une nouvelle propriété `validate` à un type de champ.
* Création d'une **classe de règles Joomla personnalisée** (`JFormRuleStrlenTen`).
* Je l'ai enregistré dans JCB en tant que fichier personnalisé.
* Compilé et testé dans votre composant.
* Ajout d'un **message d'erreur traduisible personnalisé**.

---

<a id="best-practices"></a>
### Bonnes pratiques

* Nommez toujours les fichiers de règles en **minuscules**.
* Placez tous les fichiers de règles personnalisées dans :

  ```
  administrator/components/com_componentbuilder/custom/
  ```* Gardez votre **mapping de fichiers personnalisé JCB à jour** lorsque les noms de fichiers changent.
* Utilisez des messages basés sur XML pour les composants multilingues.

---
