> **Version française expérimentale.** Traduction assistée par IA, relecture technique partielle. Les exemples de code et les destinations des liens sont conservés. Certaines procédures historiques concernent des versions antérieures de Joomla ; elles ne sont pas toutes validées pour JCB 6.2.0.

<a id="overview"></a>
## Aperçu
Joomla 5 suit le modèle de conception **Model-View-Controller (MVC)**, qui sépare le traitement des données (Modèle), la présentation (Vue) et l'interaction utilisateur (Contrôleur). Cette séparation améliore la modularité, facilitant l'extension et la maintenance des composants sans affecter les autres sections.

Le système de chargement automatique de Joomla permet aux développeurs de structurer les contrôleurs, les vues et les modèles dans des fichiers séparés sans les inclure manuellement. Cependant, des **conventions de dénomination** appropriées doivent être respectées pour garantir un chargement et une exécution fluides.

<a id="mvc-structure-in-joomla-5"></a>
## Structure MVC dans Joomla 5
<a id="file-and-naming-conventions"></a>
### **Conventions de fichiers et de dénomination**
Joomla utilise **{ComponentName}** comme référence standard pour un composant (par exemple, `Content`). Le respect de la casse est important :
- `{ComponentName}` → Format CamelCase
- `{componentname}` → Format minuscule
- `{ViewName}` → Afficher le nom dans CamelCase
- `{viewname}` → Nom de la vue en minuscules
- `{ModelName}` → Nom du modèle dans CamelCase
- `{modelname}` → Nom du modèle en minuscules
- `{ControllerName}` → Nom du contrôleur dans CamelCase
- `{controllername}` → Nom du contrôleur en minuscules

<a id="reserved-words"></a>
### **Mots réservés**
Certains mots ne peuvent pas être utilisés dans les noms de classes ou de composants. Par exemple :
- Le mot **"modèle"** ne peut apparaître que comme deuxième partie du nom d'une classe de modèle (par exemple, `ContentModelArticles`).
- Les noms de composants ne peuvent pas contenir « Modèle », car les contrôleurs héritent des conventions de dénomination des modèles.

<a id="installation-package-and-file-placement"></a>
## **Package d'installation et placement de fichiers**
Toutes les extensions Joomla doivent être empaquetées sous forme de fichier `.zip` et contenir au moins les répertoires suivants :

```
com_{componentname}/
├── site/
└── admin/
```- **`site/`** : contient les fichiers frontaux.
- **`admin/`** : contient les fichiers backend (administrateur).

Une fois installé :
- `site/` est placé sous `/components/com_{componentname}`
- `admin/` est placé sous `/administrator/components/com_{componentname}`

<a id="frontend-site-component-structure"></a>
## **Structure des composants frontend (`/site`)**

<a id="main-entry-point"></a>
### **Point d'entrée principal**
- **`site/{componentname}.php`** → Le fichier d'entrée principal du composant.

<a id="controller"></a>
### **Contrôleur**
- **`site/controller.php`** → Contrôleur par défaut.
- Définit `{ComponentName}Controller`, étendant `\Joomla\CMS\MVC\Controller\BaseController`.
- Les contrôleurs supplémentaires se trouvent sous `site/controllers/{controllername}.php`.

<a id="views"></a>
### **Vues**
- **`site/views/{viewname}/view.html.php`** → Fichier de vue principale.
- Déclare `{ComponentName}View{ViewName}` étendant `\Joomla\CMS\MVC\View\HtmlView`.
- Les modèles de vue résident dans :```
  site/views/{viewname}/tmpl/
  ├── default.php  (Main template file)
  ```

<a id="models"></a>
### **Modèles**
- **`site/models/{modelname}.php`** → Classe de modèle.
- Déclare `{ComponentName}Model{ModelName}` étendant `\Joomla\CMS\MVC\Model\BaseDatabaseModel`.
- Par défaut, une vue charge un modèle du même nom (s'il existe).

<a id="backend-admin-component-structure"></a>
## **Structure des composants back-end (`/admin`)**
Le répertoire `/admin` suit la même structure que `/site`, mais il est entièrement distinct.

Points clés :
- **Les composants d'administration et de site sont distincts** ; le partage du code est facultatif.
- Les **modèles partagés** peuvent réduire la duplication de code.
- Pour éviter les risques de sécurité, assurez-vous que les utilisateurs du site ne peuvent pas exécuter d'actions d'administration.

<a id="code-sharing-between-site-and-admin"></a>
### **Partage de code entre le site et l'administrateur**
Joomla prend en charge les modèles partagés et les classes utilitaires entre le frontend et le backend. Lors du partage de code :
- Placer les classes partagées dans un répertoire neutre (`/models`, `/helpers`).
- Assurez-vous que la conception de la classe empêche tout accès non autorisé aux fonctionnalités d'administration.

<a id="naming-validation-in-joomla-core"></a>
## **Validation du nom dans Joomla Core**
Joomla applique les règles de dénomination via la fonction `getName()` dans :
**`libraries/src/MVC/Model/BaseDatabaseModel.php`** :```php
if (!preg_match('/Model(.*)/i', get_class($this), $r)) {
    throw new RuntimeException("Invalid model class name");
}
```Cela garantit que la structure MVC appropriée est maintenue dans Joomla 5.

## **Conclusion**
En adhérant à l'architecture MVC et aux conventions de dénomination de Joomla, les développeurs peuvent créer des composants maintenables, extensibles et bien structurés. Garder la logique du site et de l'administration modulaire améliore la réutilisabilité et la sécurité au sein de l'écosystème Joomla.