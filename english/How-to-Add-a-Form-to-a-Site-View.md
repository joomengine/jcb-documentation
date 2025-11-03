# How to Add a Form to a Site View

## Introduction

> [00:00:10](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h00m10s)

In this tutorial, we demonstrate how to **add a form to a Site View** in Joomla Component Builder (JCB).
The process follows Joomla's **MVC structure** and JCB's automated generation workflow.

While it's possible to manually add a form to a Site View, **the Joomla best practice** is to use an **Admin View as a Site View**, since Joomla's core architecture expects form submissions to originate from such views.

---

## 1. Best Practice: Use an Admin View as a Site View

> [00:00:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h00m37s)

When you want to store form data into the database, the recommended way is to:

1. **Create an Admin View** that contains the form and table structure.
2. **Enable the "Create Site Edit View"** option in JCB.
   This automatically makes the Admin View accessible from the **frontend** as a Site View.

**Why this is best practice:**

* Follows Joomla's native MVC structure.
* Ensures generated code handles validation, saving, and permissions correctly.
* Reduces risk of insecure or unsupported form handling.

---

## 2. Building the Edit Link in Your Site View

> [00:01:11](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h01m11s)

To access the edit area of your Site View, you need an **Edit Link**.
This link is not auto-generated-you must add it manually.

**Steps:**

1. Go to **Dynamic GETs** in JCB.
2. Open the GET related to your Site View (e.g., `looks`).
3. Inside the dynamic GET script, retrieve the **actions** and **permissions**.
4. Build a conditional edit link using `JRoute` if the user has `core.edit` permission.

Example snippet (from video):

```php
if ($canEdit) {
    $item->edit_link = JRoute::_('index.php?option=com_example&task=item.edit&id=' . $item->id);
} else {
    $item->edit_link = '';
}
```

*Tip:* Keeping this logic inside the model (via the Dynamic GET) helps maintain MVC separation.

---

## 3. Using Existing Pagination Form

> [00:02:54](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h02m54s)

If your Site View already uses **pagination**, Joomla automatically includes a `<form>` tag around your list layout.
This means you already have a form-no need to add another.

**Steps to confirm:**

1. In JCB, open your **Site View** (e.g., `Looks`).
2. Ensure **Pagination** is set to **Yes**.
3. Compile and inspect the generated HTML:

   ```html
   <form action="index.php?option=com_example&view=looks" method="post" name="adminForm" id="adminForm">
       ...
       <input type="hidden" name="task" value="" />
       <input type="hidden" name="form_token" value="1" />
   </form>
   ```
4. You can now simply **add buttons** or **hidden inputs** within this form to capture and process submissions.

*You already have CSRF protection via Joomla's form token.*

---

## 4. Adding a Custom Submit Button

> [00:05:14](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h05m14s)

To trigger custom form actions, add a button through JCB's **button configuration**.

**Steps:**

1. Go to your **Site View** in JCB.
2. Add a new **Button**:

   * **Name:** `Submit`
   * **Icon:** e.g., `save`
   * **Task / Controller Method:** `saveMyStuff`
   * **Target Controller:** your view's controller (e.g., `looks`)
3. Add the **Custom Option** (code placeholder) to position your button inside the form layout.

When compiled, JCB will:

* Insert the button inside the existing form.
* Generate or update the related controller and model files.

---

## 5. Creating the Controller Method

> [00:06:55](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h06m55s)

After adding the button, JCB generates a **controller** with your custom method.

Typical structure:

```php
public function saveMyStuff() {
    JSession::checkToken() or jexit('Invalid Token');

    $app = JFactory::getApplication();
    $model = $this->getModel('Looks');
    $data  = $this->input->get('jform', array(), 'array');

    if (!$model->validate($data)) {
        $app->enqueueMessage('Validation failed', 'error');
        $app->setUserState('com_example.edit.looks.data', $data);
        $this->setRedirect(JRoute::_('index.php?option=com_example&view=looks', false));
        return false;
    }

    if (!$model->save($data)) {
        $app->enqueueMessage('Save failed', 'error');
        return false;
    }

    $app->enqueueMessage('Data saved successfully');
    $this->setRedirect(JRoute::_('index.php?option=com_example&view=looks', false));
}
```

**Important:** Always perform token validation and input sanitization to prevent vulnerabilities.

---

## 6. Extending the Model

> [00:09:43](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h09m43s)

Your controller calls model methods such as:

* `getForm()`
* `validate()`
* `save()`

You must implement or extend these in your **Model** file (`models/looks.php`).

If you're using dynamic or custom fields, you can build your form dynamically via code or XML.

---

## 7. Alternative Method: Add a Separate Form

> [00:16:29](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h16m29s)

For search boxes or small submission forms, you can insert a **second form** manually above the main content.

**Steps:**

1. Go to your Site View's **Custom PHP** tab in JCB.
2. Add PHP and HTML to create a standalone form:

   ```php
   <?php echo '<form id="searchForm" method="post" action="index.php?option=com_example&task=search">'; ?>
       <input type="text" name="query" placeholder="Search..." />
       <button type="submit">Search</button>
   <?php echo '</form>'; ?>
   ```
3. Compile and test.
   This form appears above the existing one without conflicts.

---

## 8. How JCB Compiles Controller & Model Code

> [00:14:32](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h14m32s)

When you compile, JCB:

* Creates or updates the controller (`controllers/looks.php`).
* Adds your new task (e.g., `saveMyStuff`) automatically.
* Updates the model with `getForm()` and related methods.

You can verify this inside the generated component files after compilation.

---

## 9. Understanding Field Building the JCB Way

> [00:21:38](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h21m38s)

JCB's compiler uses Joomla's **Form Field Objects** for building forms dynamically.

### Helper: `getFieldObject()`

This helper method automates field creation by taking:

* **Attributes** (type, name, label, description, etc.)
* **Default value**
* **Options**

It builds a valid Joomla field XML and loads it via:

```php
$field = JFormHelper::loadFieldType($attributes['type']);
$field->setup($xmlField, $value);
return $field;
```

This ensures full compatibility with Joomla's native field handling system.

---

## 10. Accessing the Compiler's Custom Admin View Example

> [00:26:20](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h26m20s)

You can study JCB's own **Compiler** component for a live example of dynamic form rendering.

**Steps:**

1. In JCB, import the **JCB component itself** via *Import JCB Package*.
2. Open the **Compiler (Custom Admin View)**.
3. Review the PHP tab to see how JCB:

   * Loads fields dynamically.
   * Uses `JText::_()` for language strings.
   * Outputs fields and controls inside a standard Joomla form.

This is an ideal reference for building your own dynamic site forms.

---

## Summary

> [00:29:37](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h29m37s)

**Adding a form to a Site View** in JCB can be done in two main ways:

| Method                              | Description                                                              | Best for                   |
| ----------------------------------- | ------------------------------------------------------------------------ | -------------------------- |
| **1. Use Existing Pagination Form** | Add buttons or fields inside Joomla's existing form structure.           | Full-page data submissions |
| **2. Custom Form Above View**       | Add separate form via PHP tab for lightweight tasks (search, filtering). | Quick interactions         |

---

## Pro Tips

* Always **validate and sanitize** input using Joomla's model validation.
* Use `JSession::checkToken()` to prevent CSRF attacks.
* Keep logic in controllers and models, not in views.
* Study JCB's Compiler View for best-practice examples.
* Avoid creating multiple forms unless absolutely needed.

---

## Conclusion

> [00:30:00](https://www.youtube.com/watch?v=UVICsD82oWk&t=00h30m00s)

By following these steps, you can safely and efficiently add forms to your JCB Site Views-leveraging Joomla's MVC structure and JCB's automation while maintaining security and clean architecture.

---
