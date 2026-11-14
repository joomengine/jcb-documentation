> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="easy-validation-rules-for-fields-in-joomla-component-builder-jcb"></a>
# Règles de validation simples pour les champs dans Joomla Component Builder (JCB)

**Source du didacticiel :** [YouTube - Règles de validation simples pour les champs dans JCB](https://www.youtube.com/watch?v=gYcZvL3u2To)
**Références d'horodatage :** Inclus dans cette documentation.

---

<a id="overview"></a>
## Aperçu

L'ajout de **règles de validation** aux champs de **Joomla Component Builder (JCB)** garantit que les données saisies dans vos formulaires répondent à des conditions spécifiques avant d'être stockées dans la base de données.

Avec les nouvelles versions de JCB, ce processus est devenu **extrêmement simple**, grâce à la **zone dédiée aux règles de validation**.
Vous pouvez désormais facilement créer, personnaliser et attribuer des règles de validation à n'importe quel champ de vos composants, sans avoir besoin de modifier manuellement le code PHP dans vos fichiers de composants.

---

<a id="what-are-validation-rules"></a>
## Que sont les règles de validation ?

> [00:00:36](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h00m36s)

Une **règle de validation** vérifie si la valeur d'un champ répond à certains critères avant de l'enregistrer.
Il s'exécute **côté serveur** et renvoie généralement :

* `true` → La valeur est valide, le formulaire est enregistré.
* `false` → La valeur n'est pas valide, le formulaire rejette la soumission avec un message d'erreur.

Ces règles sont utiles pour garantir que les valeurs telles que les e-mails, les numéros, les champs uniques ou l'existence dans une base de données sont valides avant l'enregistrement.

---

<a id="-where-to-add-validation-rules-in-jcb"></a>
## 🧭 Où ajouter des règles de validation dans JCB

> [00:01:41](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h01m41s)

Vous pouvez accéder aux règles de validation de deux manières :

1. Depuis une **configuration de champ** (par exemple, le champ "nom").
2. Directement via le **menu Règles de validation** dans JCB.

Chaque champ peut avoir une ou plusieurs règles de validation appliquées.

---

<a id="step-by-step-creating-a-custom-validation-rule"></a>
## Étape par étape : création d'une règle de validation personnalisée

<a id="step-1-open-or-create-a-field"></a>
### Étape 1 : Ouvrir ou créer un champ

Ouvrez n'importe quel champ (par exemple, le champ `name`). Vous verrez les règles de validation existantes telles que :

* `exists`
* `unique`
* Types de validation de base de Joomla comme `email`, `url`, etc.

> [00:02:04](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h02m04s)

Ceux-ci peuvent servir d’exemples ou de modèles pour votre propre règle.

---

<a id="step-2-create-a-new-validation-rule"></a>
### Étape 2 : Créer une nouvelle règle de validation

> [00:02:28](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h02m28s)

1. Cliquez sur **Créer une nouvelle règle de validation**.
2. Lorsque vous y êtes invité, cliquez sur **OK**. Vous serez redirigé vers le formulaire *Nouvelle règle de validation*.
3. Saisissez un **nom de règle unique** (par exemple, `myvalidation`).
4. Vous pouvez éventuellement ajouter une **description** pour expliquer son objectif.

> **Conseil :** Choisissez des noms descriptifs tels que `validateusername` ou `checkcustomcode` pour rendre votre code facile à reconnaître plus tard.

---

<a id="step-3-base-it-on-an-existing-rule-optional"></a>
### Étape 3 : Basez-la sur une règle existante (facultatif)

> [00:03:25](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h03m25s)

Vous pouvez choisir une **règle de base Joomla** comme base.
Cette liste déroulante vous aide à inspecter les implémentations existantes (telles que `email`, `url`, etc.) à titre de référence.

En sélectionner un ne stocke aucune donnée - il charge simplement le code dans votre éditeur comme point de départ.

Par exemple, sélectionnez **email** pour afficher la logique de validation des e-mails intégrée de Joomla.

---

<a id="step-4-write-your-php-validation-code"></a>
### Étape 4 : Écrivez votre code de validation PHP

> [00:04:12](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h04m12s)

Écrivez votre code PHP dans l'éditeur.
Vous pouvez étendre la logique de base ou créer une vérification entièrement personnalisée.

Les règles de validation sont des classes Joomla `FormRule` standard qui :

* Prolonger `Joomla\CMS\Form\FormRule`
* Remplacer la méthode `test()`

Exemple de structure (du noyau Joomla) :

```php
class JFormRuleMyValidation extends FormRule
{
    protected $regex = '^[A-Za-z0-9_]+$';
}
```

> **Remarque :** Vous devez connaître un peu PHP pour modifier ces règles efficacement.

---

<a id="step-5-save-and-close"></a>
### Étape 5 : Enregistrez et fermez

> [00:04:37](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h04m37s)

Après l'enregistrement, JCB ajoute automatiquement votre nouvelle règle à la **liste des règles de validation** et elle devient disponible pour affectation dans n'importe quel champ.

---

<a id="assigning-the-validation-rule-to-a-field"></a>
## Affectation de la règle de validation à un champ

> [00:05:01](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h05m01s)

1. Retournez à votre champ (par exemple, `name`).
2. Faites défiler jusqu'aux options **Validation**.
3. Cliquez sur **"+"** pour ajouter une règle.
4. Sélectionnez ou collez le nouveau nom de la règle (par exemple, `myvalidation`).

> [00:05:48](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h05m48s)
> Même si le champ est utilisé à plusieurs endroits, la validation s'applique globalement partout où ce champ est utilisé.

---

<a id="compiling-and-verifying-the-validation-rule"></a>
## Compilation et vérification de la règle de validation

> [00:06:18](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h06m18s)

Lorsque vous **compilez** votre composant, JCB automatiquement :

* Crée un fichier dans `/admin/models/rules/`
* Ajoute votre logique PHP à ce fichier

Par exemple:

```
admin/models/rules/myvalidation.php
```

Ce fichier étendra le `FormRule` de Joomla et contiendra votre code.

---

<a id="step-1-verify-rule-file"></a>
### Étape 1 : Vérifier le fichier de règles

Ouvrez le fichier compilé (`myvalidation.php`) et confirmez que votre code PHP est inclus.

> [00:06:42](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h06m42s)

---

<a id="step-2-check-xml-form-reference"></a>
### Étape 2 : Vérifiez la référence du formulaire XML

> [00:07:05](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h07m05s)

JCB lie également automatiquement la règle dans votre fichier de formulaire XML, par exemple :

```
admin/models/forms/customview.xml
```

Dans la définition du champ :

```xml
<field name="name" type="text" label="Name" validate="myvalidation" />
```

En haut du fichier XML, vous verrez une référence au chemin des règles :

```xml
<fields rules="components/com_yourcomponent/models/rules" />
```

---

<a id="step-3-config-file-setup"></a>
### Étape 3 : Configuration du fichier de configuration

> [00:07:56](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h07m56s)

JCB ajoute automatiquement le chemin de la règle à votre **fichier de configuration de composant**, garantissant que :

* La règle est reconnue mondialement.
* Les champs de configuration peuvent également utiliser la même validation.

Exemple:

```php
'formrules' => JPATH_ADMINISTRATOR . '/components/com_yourcomponent/models/rules',
```

---

<a id="managing-validation-rules"></a>
## Gestion des règles de validation

> [00:08:41](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h08m41s)

Vous pouvez accéder à toutes les règles créées depuis :

> **Composants → JCB → Règles de validation**

Ici, vous pouvez :

* Modifier les règles existantes.
* Ajoutez-en de nouveaux.
* Découvrez où chaque règle est utilisée dans les champs.

> [00:09:05](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h09m05s)
> Chaque règle peut être modifiée et toute modification se propagera automatiquement à tous les champs qui l'utilisent une fois recompilée.

---

<a id="key-takeaways"></a>
## Points clés à retenir

* JCB automatise l'ensemble du processus de règles de validation - de la création à l'intégration.
* Vous pouvez baser de nouvelles règles sur les règles principales de Joomla.
* Toutes les règles personnalisées sont stockées dans `/admin/models/rules/`.
* Ils sont référencés automatiquement dans les formulaires XML et les fichiers de configuration.
* La recompilation du composant met automatiquement à jour tous les champs associés.

---

<a id="example-workflow-summary"></a>
## Exemple de résumé du flux de travail

1. Ouvrez n'importe quel champ (par exemple, `name`).
2. Cliquez sur **Créer une nouvelle règle de validation**.
3. Définissez un nom de règle unique et ajoutez votre code PHP.
4. Enregistrez et attribuez la règle au champ.
5. Compilez votre composant.
6. Vérifiez le fichier généré et les références XML.
7. Réutilisez et modifiez facilement les règles de validation via l'interface JCB.

---

<a id="conclusion"></a>
## Conclusion

> [00:09:25](https://www.youtube.com/watch?v=gYcZvL3u2To&t=00h09m25s)

Le système **Validation Rule** de JCB rationalise la logique de validation dans l'ensemble de votre composant.
Vous pouvez désormais créer, réutiliser et maintenir efficacement des règles de validation, avec une intégration entièrement automatique lors de la compilation.

Cela garantit une validation des données propre et fiable qui respecte les normes de Joomla tout en restant facile à étendre et à maintenir.

---
