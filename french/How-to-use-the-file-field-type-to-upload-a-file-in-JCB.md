> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="how-to-use-the-file-field-type-to-upload-a-file-in-jcb"></a>
# Comment utiliser le type de champ de fichier pour télécharger un fichier dans JCB

<a id="overview"></a>
### Aperçu

Ce guide explique comment utiliser correctement le **Type de champ de fichier** dans Joomla Component Builder (JCB) pour activer les téléchargements de fichiers dans votre composant. Vous apprendrez à ajouter et à configurer le champ de fichier, à implémenter la validation et le déplacement côté serveur et à afficher dynamiquement le fichier téléchargé dans la vue administrateur.

---

<a id="1-adding-a-file-field-to-a-component"></a>
## 1. Ajout d'un champ de fichier à un composant

**Horodatage :** [00:00:00](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h00m00s)

Nous commençons par ajouter un champ de téléchargement de fichier à un composant. Dans cet exemple, le **composant de démonstration** est utilisé, qui comprend plusieurs vues d'administration telles que `Look` et des vues de site telles que `Looks` et `Looking`.

Nous ajouterons notre **champ de fichier** à la vue administrateur `Look`.

> **Remarque :** JCB ne gère pas automatiquement les téléchargements de fichiers pour des raisons de sécurité. Vous implémenterez cette logique manuellement pour conserver un contrôle total.

---

<a id="2-using-the-existing-file-fieldtype"></a>
## 2. Utilisation du type de champ de fichier existant

**Horodatage :** [00:01:06](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h01m06s)

JCB fournit déjà un type de champ **Fichier**. Accédez à :

> `Component Builder → Fieldtypes → File`

Ici, vous verrez les attributs de champ tels que définis dans la documentation de Joomla. Passez en revue les options disponibles telles que :

* **Accepter**
* **Taille**
* **Plusieurs**
* **Répertoire**

> Le paramètre **Accepter** (par exemple, `image/*`) spécifie les types de fichiers autorisés pour le téléchargement.

Si ce paramètre est manquant dans votre version, ajoutez-le manuellement.

---

<a id="3-adding-the-accept-attribute-optional-update"></a>
## 3. Ajout de l'attribut "Accepter" (mise à jour facultative)

**Horodatage :** [00:02:30](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h02m30s)

Si votre version JCB ne dispose pas de l'attribut `accept` :

1. Ajoutez-le manuellement sous « Taille ».
2. Définissez sa valeur par défaut sur `image/*`.
3. Fournissez une description (par exemple, « Types de fichiers autorisés »).

Enregistrez et fermez le type de champ.

---

<a id="4-creating-and-configuring-the-file-field"></a>
## 4. Création et configuration du champ de fichier

**Horodatage :** [00:03:19](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h03m19s)

Go to:

> `Component Builder → Fields → New`

Définissez les éléments suivants :

* **Nom :** `banner`
* **Étiquette :** `Banner`
* **Type :** `File`
* **Description :** "Téléchargez une image depuis votre ordinateur (max 100 Ko)."

Enregistrez et fermez.

---

<a id="5-assigning-the-file-field-to-an-admin-view"></a>
## 5. Attribution du champ de fichier à une vue administrateur

**Horodatage :** [00:04:54](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h04m54s)

1. Ouvrez la vue Admin de votre composant (`Look`).
2. Cliquez sur **Champs**.
3. Ajoutez le nouveau champ `Banner (file)` sous l'**onglet** souhaité (par exemple, « Plus »).
4. Définissez **Alignement** sur *Pleine largeur*.
5. Enregistrez et fermez.

> **Conseil :** Évitez les noms de champs en double. Chaque champ doit avoir un `Name` unique pour éviter les problèmes de suivi de l'historique.

Compilez et installez votre composant, puis vérifiez que le champ apparaît correctement.

---

<a id="6-understanding-why-the-file-isnt-uploaded-yet"></a>
## 6. Comprendre pourquoi le fichier n'est pas encore téléchargé

**Horodatage :** [00:09:56](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h09m56s)

Lorsque vous enregistrez un élément, vous remarquerez que le fichier n'est pas encore téléchargé sur votre serveur.
En effet, JCB n'inclut pas de **logique de téléchargement côté serveur** par défaut. Vous devrez :

* Valider le dossier
* Déplacez-le vers le dossier souhaité
* Vérifiez-le et désinfectez-le
* Enregistrez son chemin vers la base de données

---

<a id="7-adding-server-side-file-handling-code"></a>
## 7. Ajout du code de gestion des fichiers côté serveur

**Horodatage :** [00:11:27](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h11m27s)

Ouvrez le fichier **Model** de votre composant dans votre IDE :

```
administrator/components/com_demo/models/look.php
```

Localisez la fonction `save()`. C'est ici que les données du formulaire sont traitées.
Vous allez insérer votre logique de gestion de fichiers ici.

---

<a id="71-inspecting-input-data"></a>
### 7.1 Inspection des données d'entrée

Utilisez un débogage rapide :

```php
var_dump($data);
var_dump($input->files->get('jform'));
```

Cela révèle quelles données de fichier Joomla reçoit lors de la soumission du formulaire.

---

<a id="72-copy-joomlas-upload-handling-function"></a>
### 7.2 Copier la fonction de gestion des téléchargements de Joomla

**Horodatage :** [00:16:58](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h16m58s)

Recherchez et copiez la fonction `getPackageFromUpload` à partir de :

```
/administrator/components/com_installer/models/install.php
```

Renommez-le en quelque chose comme :

```php
public function myUploadFunction($input)
```

Modifiez-le pour :

* Gérer les téléchargements d'images (`jpg`, `jpeg`, `png`, `gif`)
* Ignorer la logique zlib/unzip
* Inclure des vérifications pour la taille et le type de téléchargement
* Utilisez `JFile::upload($tmp_src, $tmp_dest, false, true)` pour déplacer le fichier

---

<a id="73-add-validation-and-cleanup"></a>
### 7.3 Ajouter une validation et un nettoyage

* Créez une fonction d'assistance `checkUpload()` pour valider le type de fichier.
* Ajoutez une fonction `removeFile()` pour supprimer les fichiers dont la validation échoue.

Exemple (simplifié) :

```php
public function removeFile($path)
{
    jimport('joomla.filesystem.file');
    if (JFile::exists($path)) {
        JFile::delete($path);
    }
}
```

---

<a id="8-moving-the-file-to-its-final-location"></a>
## 8. Déplacer le fichier vers son emplacement final

**Horodatage :** [00:37:14](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h37m14s)

Une fois la validation réussie, déplacez le fichier du dossier temporaire Joomla vers un répertoire permanent :

```php
JFile::move($tmp_dest, JPATH_ROOT . '/images/' . $filename);
```

Enregistrez le chemin relatif du fichier (`/images/filename.jpg`) dans le champ de la base de données.

---

<a id="9-adding-custom-php-to-jcb"></a>
## 9. Ajout de PHP personnalisé à JCB

**Horodatage :** [00:46:09](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h46m09s)

De retour chez JCB :

1. Ouvrez votre vue administrateur (`Look`).
2. Accédez à **Boutons personnalisés** → **PHP (méthode modèle)**.
3. Collez vos fonctions d'assistance (`myUploadFunction`, `checkUpload`, `removeFile`) ici.
4. Dans **Ajouter PHP (méthode de sauvegarde - avant la modélisation des données)**, insérez :

   ```php
   $package = $this->myUploadFunction($input);
   $data['banner'] = $package['dir'] . '/' . $package['name'];
   ```

Enregistrez vos modifications.

---

<a id="10-displaying-the-uploaded-file-in-the-admin-view"></a>
## 10. Affichage du fichier téléchargé dans la vue administrateur

**Horodatage :** [00:50:13](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h50m13s)

Pour prévisualiser l'image téléchargée dans le formulaire d'édition :

1. Dans la même vue d'administration, ajoutez ce qui suit dans **Ajouter du JavaScript (pied de page)** :

   ```php
   <?php if (isset($this->item->banner) && is_string($this->item->banner)) : ?>
   <script>
       jQuery(document).ready(function() {
           jQuery('#jform_banner').after('<img src="<?php echo $this->item->banner; ?>" class="preview-banner" alt="Banner Preview" />');
       });
   </script>
   <?php endif; ?>
   ```

2. Ajoutez un style via **Ajouter CSS (vue)** pour formater proprement l'aperçu de l'image.

Recompilez et réinstallez votre composant.

---

<a id="11-testing-the-result"></a>
## 11. Tester le résultat

**Horodatage :** [00:58:59](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h58m59s)

1. Ouvrez la vue Administrateur (`Look`).
2. Téléchargez un fichier et cliquez sur **Enregistrer**.
3. Le fichier devrait maintenant :

* Téléchargez avec succès
   * Déplacer vers `/images/`
   * Stocker son chemin dans la base de données
   * Affichage dans le formulaire après enregistrement

> Si vous modifiez l'image, la nouvelle remplace l'aperçu, mais vous devrez peut-être toujours supprimer manuellement l'ancien fichier (une logique personnalisée peut automatiser cette opération).

---

<a id="12-conclusion"></a>
## 12. Conclusion

**Horodatage :** [01:00:11](https://www.youtube.com/watch?v=o482sK4DxkM&t=01h00m11s)

Vous avez maintenant implémenté un **Système de téléchargement de champs de fichiers** fonctionnel au sein de JCB en utilisant les fonctionnalités natives de Joomla.
Pour référence, vous pouvez trouver la logique de téléchargement PHP finale sous forme de GitHub Gist fourni par l'auteur du didacticiel.

> **Astuce :** Pour une sécurité renforcée, validez le type MIME à l'aide des fonctions d'image Joomla ou PHP.
> Pour une prise en charge de téléchargement plus large (par exemple, PDF), ajustez les extensions autorisées dans votre logique `checkUpload()`.

---

<a id="key-takeaways"></a>
### Points clés à retenir

* Implémentez toujours la validation côté serveur pour les téléchargements.
* Utilisez les classes `JFile` et `JFolder` pour déplacer et nettoyer les fichiers en toute sécurité.
* Ajoutez des méthodes d'assistance pour garder votre modèle propre et réutilisable.
* Utilisez les **sections PHP personnalisées** de JCB pour inclure en toute sécurité une logique personnalisée lors de la compilation.

---
