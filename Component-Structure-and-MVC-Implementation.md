## Overview
Joomla 5 follows the **Model-View-Controller (MVC)** design pattern, which separates data processing (Model), presentation (View), and user interaction (Controller). This separation enhances modularity, making it easier to extend and maintain components without affecting other sections.

Joomla's autoloading system allows developers to structure controllers, views, and models in separate files without manually including them. However, proper **naming conventions** must be followed to ensure smooth loading and execution.

## MVC Structure in Joomla 5
### **File and Naming Conventions**
Joomla uses **{ComponentName}** as the standard reference for a component (e.g., `Content`). Case sensitivity is important:
- `{ComponentName}` → CamelCase format
- `{componentname}` → Lowercase format
- `{ViewName}` → View name in CamelCase
- `{viewname}` → Lowercase view name
- `{ModelName}` → Model name in CamelCase
- `{modelname}` → Lowercase model name
- `{ControllerName}` → Controller name in CamelCase
- `{controllername}` → Lowercase controller name

### **Reserved Words**
Certain words cannot be used as part of class or component names. For example:
- The word **"model"** can only appear as the second part of a model class name (e.g., `ContentModelArticles`).
- Component names cannot contain "Model," as controllers inherit naming conventions from models.

## **Installation Package and File Placement**
All Joomla extensions must be packaged as a `.zip` file and contain at least the following directories:

```
com_{componentname}/
├── site/
└── admin/
```
- **`site/`**: Holds frontend files.
- **`admin/`**: Holds backend (administrator) files.

When installed:
- `site/` is placed under `/components/com_{componentname}`
- `admin/` is placed under `/administrator/components/com_{componentname}`

## **Frontend (`/site`) Component Structure**

### **Main Entry Point**
- **`site/{componentname}.php`** → The component's main entry file.

### **Controller**
- **`site/controller.php`** → Default controller.
- Defines `{ComponentName}Controller`, extending `\Joomla\CMS\MVC\Controller\BaseController`.
- Additional controllers go under `site/controllers/{controllername}.php`.

### **Views**
- **`site/views/{viewname}/view.html.php`** → Main view file.
- Declares `{ComponentName}View{ViewName}` extending `\Joomla\CMS\MVC\View\HtmlView`.
- Templates for the view reside in:
  ```
  site/views/{viewname}/tmpl/
  ├── default.php  (Main template file)
  ```

### **Models**
- **`site/models/{modelname}.php`** → Model class.
- Declares `{ComponentName}Model{ModelName}` extending `\Joomla\CMS\MVC\Model\BaseDatabaseModel`.
- By default, a view loads a model with the same name (if it exists).

## **Backend (`/admin`) Component Structure**
The `/admin` directory follows the same structure as `/site`, but it is entirely separate.

Key points:
- **Admin and site components are distinct**; sharing code is optional.
- **Shared models** can reduce code duplication.
- To avoid security risks, ensure site users cannot execute admin actions.

### **Code Sharing Between Site and Admin**
Joomla supports shared models and utility classes between frontend and backend. When sharing code:
- Place shared classes in a neutral directory (`/models`, `/helpers`).
- Ensure class design prevents unauthorized access to admin functionalities.

## **Naming Validation in Joomla Core**
Joomla enforces naming rules via the `getName()` function in:
**`libraries/src/MVC/Model/BaseDatabaseModel.php`**:
```php
if (!preg_match('/Model(.*)/i', get_class($this), $r)) {
    throw new RuntimeException("Invalid model class name");
}
```
This ensures proper MVC structure is maintained in Joomla 5.

## **Conclusion**
By adhering to Joomla's MVC architecture and naming conventions, developers can build maintainable, extensible, and well-structured components. Keeping site and admin logic modular improves reusability and security within the Joomla ecosystem.