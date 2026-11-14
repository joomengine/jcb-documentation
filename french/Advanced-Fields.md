> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="advanced-fields---joomla-component-builder-jcb"></a>
# Champs avancés - Joomla Component Builder (JCB)

<a id="video-tutorialhttpswwwyoutubecomwatchvvpzybifqv0mlistplqrgfi8xz_wtgvpqzwbfdzzlerlqgpmret00h00m00s"></a>
### [Tutoriel vidéo](https://www.youtube.com/watch?v=VpzYbifqv0M&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

(*Cliquez sur les horodatages ci-dessous pour regarder des sections spécifiques du didacticiel.*)

---

<a id="overview"></a>
## Aperçu

Joomla Component Builder (JCB) prend en charge une variété de types de champs, notamment les champs **de base**, **dynamiques** et **avancés personnalisés**.
Ce guide se concentre sur les **champs avancés**, expliquant comment étendre la fonctionnalité des champs de Joomla en créant des champs personnalisés pilotés par PHP, en gérant les paramètres globaux, les ensembles de champs répétables et en liant dynamiquement les données entre les vues.

Les champs avancés vous permettent de :

* Remplir dynamiquement les options en utilisant la logique PHP
* Paramètres globaux des composants de référence
* Étendre les types de champs par défaut de Joomla
* Créer des structures reproductibles
* Restreindre ou filtrer les données de manière dynamique (par exemple, listes d'utilisateurs ou de prédicateurs)

---

<a id="1-setting-up-a-local-folder-field"></a>
## 1. Configuration d'un champ de dossier local

[00:00:38](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h00m38s)

<a id="purpose"></a>
### But

Ce type de champ répertorie dynamiquement les fichiers d'un **répertoire local**, en fonction des paramètres globaux de votre composant.

<a id="steps"></a>
### Étapes

1. Créez un **champ personnalisé** dans JCB et définissez son type pour étendre le champ `list`.

2. Dans la **définition du champ XML**, écrivez du PHP personnalisé dans :

* Lisez le chemin du dossier à partir des **paramètres globaux** de votre composant (par exemple, `localfolder`).
   * Vérifiez si le dossier existe ; sinon, créez-le en utilisant la classe `JFolder` de Joomla.
   * Récupérez tous les noms de fichiers et remplissez-les dans un **tableau d'options**.

3. Renvoyez ce tableau à Joomla pour le rendu sous forme de liste déroulante.

```php
$options = [];
$files = JFolder::files($path);
foreach ($files as $file) {
    $options[] = JHtml::_('select.option', $file, $file);
}
return $options;
```

**Conseil :**
Lorsque vous activez les **sélections multiples**, assurez-vous que le champ est stocké sous le nom `JSON`. JCB détectera automatiquement plusieurs valeurs et les stockera correctement.

---

<a id="2-building-a-sermon-preacher-custom-field"></a>
## 2. Création d'un champ personnalisé "Sermon Preacher"

[00:05:32](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h05m32s)

Cet exemple montre un champ qui affiche une liste de **prédicateurs** à partir de la vue de liste `preachers`.

<a id="key-conventions"></a>
### Conventions clés

* **Type de nom** : nom de vue au pluriel (par exemple, `preachers`)
* **Nom d'édition** : singulier (par exemple, `preacher`)
* **Multiple** : défini sur `false` (sélection unique)
* Utilisez un **libellé** descriptif et une **info-bulle** pour plus de clarté pour l'utilisateur.

---

<a id="3-understanding-jformfield-extensions"></a>
## 3. Comprendre les extensions `JFormField`

[00:07:02](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h07m02s)

Les champs personnalisés dans JCB **étendent généralement les classes `JFormField` natives de Joomla** telles que :

* `JFormFieldList`
* `JFormFieldUser`
* `JFormFieldRadio`
* `JFormFieldCheckbox`

Ceux-ci sont définis dans **`administrator/components/com_componentbuilder/compiler/joomla_3`**.
Vous pouvez en explorer ou en ajouter de nouveaux si votre projet nécessite des comportements uniques.

---

<a id="4-extending-list-fields-dynamically"></a>
## 4. Extension dynamique des champs de liste

[00:09:16](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h09m16s)

Lorsque vous ciblez des données d'une autre table (par exemple, `preachers`), utilisez des espaces réservés pour rendre votre composant **indépendant du nom**.

<a id="placeholder-syntax"></a>
### Syntaxe des espaces réservés

* `###component###` → remplacé par le nom réel du composant lors de la compilation.
* Utilisez toujours des **noms de vue en minuscules**.
* Utilisez correctement les champs **key** (stockés dans la base de données) et **value** (affichés dans l'interface utilisateur).

<a id="example"></a>
### Exemple

| Propriété | Descriptif |
| ----------- | ----------------------------- |
| Tableau | `#__###component###_preacher` |
| Champ clé | `id` |
| Champ de valeur | `name` |
| Nom du champ | `preacher` |

**Résultat :** Une fois compilé, le champ de liste affiche dynamiquement tous les prédicateurs pour la sélection.

---

<a id="5-adding-custom-php-in-field-definitions"></a>
## 5. Ajout de PHP personnalisé dans les définitions de champs

[00:15:59](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h15m59s)

Vous pouvez injecter PHP directement dans les définitions de champs pour affiner la logique.
**Utilisez uniquement des guillemets simples** dans votre PHP pour éviter d'échapper aux problèmes.

```php
$options[] = array('value' => $file, 'text' => $file);
```

---

<a id="6-compiling-and-code-replacement"></a>
## 6. Compilation et remplacement de code

[00:16:51](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h16m51s)

Lors de la compilation, JCB remplace les espaces réservés (comme `###ID###`, `###name###` et `###component###`) par les données réelles des composants.
Cela garantit un code réutilisable sur plusieurs composants.

**Conseil :**
Vous pouvez inspecter les fichiers compilés sous :

```
administrator/components/com_componentbuilder/helpers/compiler
```

---

<a id="7-dropbox-file-list---external-data-example"></a>
## 7. Liste de fichiers Dropbox - Exemple de données externes

[00:22:31](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h22m31s)

Exemple d'intégration d'une méthode d'assistance personnalisée (`getDropboxlinks`) pour récupérer des données à partir de sources externes comme Dropbox.
Il crée dynamiquement une liste déroulante basée sur les liens récupérés.

---

<a id="8-component-helper-classes"></a>
## 8. Classes d'assistance aux composants

[00:23:32](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h23m32s)

Chaque composant JCB comprend des **classes d'assistance** situées dans :

```
/administrator/helpers/
```

et

```
/site/helpers/
```

Ceux-ci peuvent contenir des fonctions statiques utilisées dans des champs personnalisés.

Les méthodes d'assistance intégrées courantes incluent :

* `getVar()` et `getVars()` - Récupérez les variables des composants.
* `isPublished()` - Vérifiez si un objet est publié.
* `jsonToString()` - Convertissez les objets JSON en chaînes en toute sécurité.

Vous pouvez étendre ces assistants avec votre propre logique.

---

<a id="9-custom-user-fields"></a>
## 9. Champs utilisateur personnalisés

[00:31:02](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h31m02s)

<a id="purpose-1"></a>
### But

Affichez et filtrez les utilisateurs de Joomla de manière dynamique.

<a id="features"></a>
### Caractéristiques

* Restreindre les utilisateurs par **groupe** à l'aide des paramètres globaux.
* Exclure les utilisateurs spécifiques déjà affectés à d'autres enregistrements.
* Assurez-vous d'utiliser la logique **un enregistrement par utilisateur** en utilisant PHP dans `type_phpx`.

```php
$excluded = $this->getExcludedUsers();
$options = array_diff($allUsers, $excluded);
```

**Important :**
Définissez la logique de groupe ou de restriction dans vos **Options globales**.
Accédez-y en PHP en utilisant :

```php
$group = ComponentHelper::getParams('com_example')->get('user_group');
```

---

<a id="10-naming-conventions"></a>
## 10. Conventions de dénomination

[00:38:08](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h38m08s)

Lorsque vous nommez des types de champs personnalisés :

* **Pas de traits de soulignement ni d'espaces**
* Utilisez uniquement des minuscules
* Les noms de fichiers et les types de champs doivent correspondre

Exemple :
Type de champ `studentusers` → Nom de fichier `studentusers.php`

---

<a id="11-repeatable-custom-fields"></a>
## 11. Champs personnalisés répétables

[00:40:38](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h40m38s)

<a id="concept"></a>
### Concept

Les champs répétables sont des conteneurs contenant plusieurs sous-champs.

<a id="how-to-create-one"></a>
### Comment en créer un

1. Créez les champs que vous souhaitez répéter.
2. Notez leurs **ID de champ** dans la colonne de droite.
3. Ajoutez un nouveau champ de type **répétable** et répertoriez les ID (séparés par des virgules) dans l'entrée **"Champs"**.

**Remarque :** Vous ne pouvez pas imbriquer des champs répétables, mais vous pouvez y inclure des champs personnalisés avancés.

---

<a id="12-custom-icons-for-buttons"></a>
## 12. Icônes personnalisées pour les boutons

[00:44:41](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h44m41s)

Utilisez les [icônes de police Icomoon](https://docs.joomla.org/J3.x:Joomla_Standard_Icomoon_fonts) de Joomla pour personnaliser les boutons.

Exemple:

```xml
<field name="add" label="Add" icon="checkmark-circle" />
```

---

<a id="13-radio-buttons-in-repeatable-fields"></a>
## 13. Boutons radio dans les champs répétables

[00:47:39](https://www.youtube.com/watch?v=VpzYbifqv0M&t=00h47m39s)

Lors de l'utilisation de **boutons radio** dans des champs répétables :

* Supprimez la **classe CSS "bouton"**.
* Utilisez la **radio de style point** (`Searchable Yes/No`) au lieu du style bouton pour éviter les problèmes de rendu.

---

<a id="summary"></a>
## Résumé

| Concepts | Aperçu clé |
| ------------------------- | -------------------------------------------------------------------- |
| **Types de champs personnalisés** | Étendre les champs de liste de Joomla pour les données dynamiques |
| **Intégration globale** | Accéder aux paramètres au niveau des composants à l'aide des assistants |
| **Structures répétables** | Combinez plusieurs champs dans un conteneur répétable |
| **Logique PHP dynamique** | Remplir les listes déroulantes ou filtrer les données de manière dynamique |
| **Règles de dénomination** | Minuscules, pas de traits de soulignement, cohérents avec les noms de vues |

---

<a id="final-notes"></a>
### Notes finales

* **Compilez** toujours votre composant après avoir ajouté ou modifié des champs personnalisés.
* Testez votre logique de champ en inspectant les fichiers PHP compilés.
* Utilisez les espaces réservés de JCB (`###component###`) pour conserver la flexibilité lors du renommage des composants.
* Pour plus d'exemples ou de dépannage, reportez-vous aux forums JCB ou aux discussions GitHub.

---
