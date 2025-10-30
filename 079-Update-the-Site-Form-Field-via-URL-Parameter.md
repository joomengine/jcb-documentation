# Update the Site Form Field via URL Parameter

## Overview

In this tutorial, we'll learn how to **add a form to a site view** in Joomla Component Builder (JCB), manage its submission through a **controller**, and dynamically link it with the **model** for validation and saving.
We'll also see how JCB helps generate much of the needed code automatically - including **buttons**, **controllers**, and **model methods** - while keeping the MVC structure intact.

> **[00:00:10](https://www.youtube.com/watch?v=UVICsD82oWk&t=10s)**

---

## 1. Using an Admin View as a Site View

> **[00:00:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=37s)**

Best practice in Joomla is to use an **Admin View as a Site View** for forms that store data in the database.

### Why This Is Recommended

* **Joomla's MVC structure** is optimized for this approach.
* The same Admin view logic can be extended for the frontend.
* Data submission (saving to the database) is already built into the Admin architecture.

To create a Site View from an Admin View:

1. Open your component in **JCB**.
2. Locate your **Admin View**.
3. Tick the option **"Create Site View for this Admin View"**.
4. JCB automatically generates the corresponding **Site View**.

---

## 2. Creating an Edit Link for Site View

> **[00:01:11](https://www.youtube.com/watch?v=UVICsD82oWk&t=71s)**

The site edit area isn't auto-generated; you need to create a **dynamic edit link** manually.

### Steps:

1. Go to **Dynamic GETs** in JCB.
2. Open the GET query for your site view (e.g., `Looks`).
3. Add code to:

   * Fetch **user permissions** (e.g., canEdit).
   * If true, build a link with `JRoute`.
   * Include the task and target route.

Example snippet (from tutorial):

```php
if ($canEdit) {
  $link = JRoute::_('index.php?option=com_yourcomponent&task=look.edit&id=' . $item->id);
} else {
  $link = '';
}
```

> *Tip:* Keep data modeling separate from display logic - build links in the model layer, not in the view.

---

## 3. Using the Existing Form with Pagination

> **[00:03:22](https://www.youtube.com/watch?v=UVICsD82oWk&t=202s)**

If your site view already has **pagination**, JCB automatically generates a `<form>` tag around the list.

You **don't need to add another form** - simply add inputs or buttons inside it.

### How It Works

* Pagination = automatic `<form>` creation.
* The form includes:

  * `name` and `id` attributes.
  * A `form token` for security.
  * `action` pointing to your component.

Example generated structure:

```html
<form action="index.php?option=com_yourcomponent" method="post" id="adminForm" name="adminForm">
  <!-- Your fields and buttons here -->
  <?php echo JHtml::_('form.token'); ?>
</form>
```

You can insert your own submit button:

```html
<button type="submit" class="btn btn-success">Submit</button>
```

Then use JavaScript or controller logic to process the form task.

---

## 4. Adding a Custom Button in JCB

> 🕒 **[00:05:38](https://www.youtube.com/watch?v=UVICsD82oWk&t=338s)**

You can add a **custom button** directly within JCB.

### Steps:

1. Open your **Site View**.
2. In **Buttons**, click **Add Button**.
3. Set:

   * **Button Name:** e.g., `Submit`
   * **Icon:** choose from list
   * **Target Controller Method:** e.g., `saveMyStuff`
   * **Button Type:** Default (leave unchanged)
4. Use **Custom Option → Copy → Paste** to control button placement.

This automatically sets up:

* The **controller** and **method name**.
* The **toolbar** button.
* The corresponding **model link**.

After compiling, check the generated:

* `/controllers/look.php` – new controller with your method.
* `/models/look.php` – includes the model methods (e.g., `getForm`, `validate`, `save`).

---

## 5. Understanding the Controller Logic

> 🕒 **[00:07:18](https://www.youtube.com/watch?v=UVICsD82oWk&t=438s)**

Each form submission triggers a **controller method**.

Controller handles:

1. **Token validation** for security.
2. **Input retrieval** from `JInput`.
3. **Model access** via `getModel()`.
4. **Form validation and saving**.
5. **Redirects** after completion.

### Example Flow:

```php
public function saveMyStuff() {
  JSession::checkToken() or jexit('Invalid Token');
  $app = JFactory::getApplication();
  $model = $this->getModel('Look');
  $data = $app->input->get('jform', [], 'array');

  $form = $model->getForm($data, false);
  $validated = $model->validate($form, $data);

  if ($validated === false) {
    $errors = $model->getErrors();
    foreach ($errors as $error) {
      $app->enqueueMessage($error, 'warning');
    }
    $app->setUserState('com_yourcomponent.edit.look.data', $data);
    $this->setRedirect(JRoute::_('index.php?option=com_yourcomponent&view=look&layout=edit', false));
    return false;
  }

  $model->save($validated);
  $app->enqueueMessage('Saved successfully', 'message');
  $this->setRedirect(JRoute::_('index.php?option=com_yourcomponent&view=looks', false));
}
```

> *Always include validation and CSRF checks.*

---

## 6. Model Integration

> **[00:10:17](https://www.youtube.com/watch?v=UVICsD82oWk&t=617s)**

You'll need to manually add the supporting methods to your **model**:

* `getForm()`
* `validate()`
* `save()`

For dynamic forms (not static XML), JCB supports **runtime-generated XML** forms.

---

## 7. Example of Dynamic Form XML Builder

> **[00:11:31](https://www.youtube.com/watch?v=UVICsD82oWk&t=691s)**

JCB's compiler component demonstrates how to **dynamically build XML form fields**.

```php
$field = $helper->getFieldObject($attributes, $defaultValue, $options);
```

### Helper Workflow

* Creates XML structure.
* Adds attributes and options.
* Loads the Joomla field type dynamically.

Use this approach to build dynamic field structures within your models.

---

## 8. Custom PHP in Site View

> 🕒 **[00:16:54](https://www.youtube.com/watch?v=UVICsD82oWk&t=1014s)**

For more control, use **Custom PHP view script**.

### Steps:

1. Open your **Site View**.
2. In the **PHP Tab**, add your custom script.
3. Insert your form above the default form using PHP break-out syntax:

   ```php
   ?> 
   <form id="myCustomForm">
     ...
   </form>
   <?php
   ```
4. Make sure form `name` and `id` are unique.

---

## 9. Best Practices for Form Building in JCB

> 🕒 **[00:21:38](https://www.youtube.com/watch?v=UVICsD82oWk&t=1298s)**

* Always use **JCB's helper classes** (`getFieldObject`, etc.).
* Let **Joomla handle rendering and token management**.
* Keep form logic within **MVC structure**.
* Validate every input in the **controller and model**.
* Sanitize user input properly.

---

## 10. Using JCB's Own Compiler as a Reference

> **[00:25:48](https://www.youtube.com/watch?v=UVICsD82oWk&t=1548s)**

You can **import the JCB component into JCB** itself to study how its compiler handles forms.

1. Go to **Components → Joomla Components**.
2. Click **Import JCB Package**.
3. Select the `Component Builder` package.
4. Add your **license key**.
5. Continue import.

Open the **compiler view** and study:

* PHP methods that generate fields.
* How labels and language strings are managed.
* How the `JText::_()` function maps labels to language constants.

---

## Summary

| Task               | Area           | Description                                 |
| ------------------ | -------------- | ------------------------------------------- |
| Create Site Form   | Site View      | Enable form by reusing pagination form      |
| Add Button         | JCB Buttons UI | Create "Submit" button tied to controller   |
| Build Controller   | Auto / Manual  | Handles submission, validation, redirect    |
| Add Model Logic    | Model          | Include `getForm()`, `validate()`, `save()` |
| Use Dynamic Fields | Helper         | Use `getFieldObject()` for XML generation   |
| Add Custom PHP     | PHP Tab        | Insert form markup above/below list         |
| Test & Compile     | Compiler       | Build and install to test functionality     |

---

## Pro Tips

* Use **JCB Buttons** to generate scaffolding quickly.
* Always compile after making structure changes.
* Avoid duplicating `<form>` tags inside paginated lists.
* Review JCB's own **Compiler admin view** for advanced form rendering patterns.
* Use **language constants** for field labels (`COM_COMPONENT_FIELD_LABEL`).

---

## Closing Notes

> **[00:29:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=1777s)**

This method ensures:

* Fully MVC-compliant forms.
* Cleaner integration with Joomla.
* Automated controller/model code generation.
* Maintainable, secure frontend form handling.
