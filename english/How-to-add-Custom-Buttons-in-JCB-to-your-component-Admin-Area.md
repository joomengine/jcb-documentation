# How to Add Custom Buttons in JCB to Your Component Admin Area

This guide explains how to **add custom buttons** to your Joomla Component Builder (JCB) components - both in **List Views** and **Edit Views** - using JCB's interface without custom PHP overrides.
You'll also learn how these buttons integrate with **controllers, models**, and Joomla's **permission system**, following MVC principles.

> *Based on the video tutorial: [How to Add Custom Buttons in JCB to Your Component Admin Area](https://www.youtube.com/watch?v=VyBxWpJWb40)*
> (*Click on timestamps to jump to that moment in the video.*)

---

## Overview

[00:00:00](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h00m00s)

This tutorial demonstrates how to add buttons to either:

* The **Admin List View** toolbar, or
* The **Edit View** toolbar.

These buttons allow you to trigger custom controller methods - e.g., redirect users, run custom logic, or modify data - directly from the Joomla admin interface, without manual code edits.

---

## 1. Preparing the Environment

[00:00:38](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h00m38s)

1. Open a **clean Joomla site** with JCB installed.
2. Ensure your **demo component** is already mapped and installed.
3. Open your component from the **Joomla Administrator** panel.
4. Navigate to any view (e.g., `Looks`) to confirm it displays the standard Joomla buttons (`New`, `Edit`, `Publish`, `Unpublish`, etc.).

Your goal will be to add **new custom buttons** here using JCB.

---

## 2. Navigating to Custom Buttons in JCB

[00:01:19](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h01m19s)

1. In JCB, go to **Admin Views**.
2. Open the desired view (e.g., `Look`).
3. Locate the **Custom Buttons** section.
4. Click **"Yes"** when asked to add a custom button.

---

## 3. Understanding the MVC Relationship

[00:02:05](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h02m05s)

Each Admin View in JCB is backed by:

* A **List view** controller and model, and
* An **Edit view** controller and model.

Depending on where your button appears, JCB will automatically place the PHP method in the correct controller and model files:

* Buttons in the **list view** affect multiple records.
* Buttons in the **edit view** act on a single item.

> **Tip:** Familiarity with Joomla's MVC API helps you understand how the generated PHP logic fits together.

---

## 4. Creating a Custom Button

[00:03:07](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h03m07s)

Follow these steps to add your first custom button:

1. In **Custom Buttons**, click **"Add"**.
2. Set:

   * **Icon:** Choose from Joomla's default *Icomoon* icons.
   * **Name:** For example, `Test`.
   * **Controller Method Name:** For example, `getTested`.
3. **Target View Type:** Choose where the button appears:

   * `list`
   * `single`
   * `both`
4. **Type:**

   * `Function` - runs directly when clicked.
   * `Selection` - requires selected rows to pass IDs.
   * `Default` - similar to selection but with flexible behavior.

Save your button.

---

## 5. Writing the Controller Method

[00:05:05](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h05m05s)

When compiled, JCB automatically creates the PHP method in the correct controller file.

Example:

```php
public function getTested()
{
    // Verify request origin
    if (!JSession::checkToken()) {
        jexit('Invalid Token');
    }

    // Redirect to dashboard
    $this->setRedirect(JRoute::_('index.php?option=com_demo', false));
}
```

> **How JCB handles empty blocks:**
> If no code is added, JCB inserts placeholder slashes `//` to maintain structure.

Compile and install your component.
Go to **Components → Demo → Looks** - your new **Test** button appears.
Clicking it will redirect to the dashboard.

---

## 6. Adding a Button to the Edit View

[00:07:05](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h07m05s)

To create a button inside the **Edit View**:

1. Add another custom button.

   * **Target:** `single`
   * **Name:** `Work`
   * **Controller Method:** `getDone`
   * **Type:** `Default`
2. In your controller method, JCB inserts:

```php
public function getDone()
{
    // Access the model
    $model = $this->getModel();
    $data  = $model->getData();

    // Perform your logic, then redirect or return status
}
```

You can:

* Validate item data,
* Perform operations on it,
* Use `$model->save($data)` to store updated values.

---

## 7. Validating and Triggering the Model

[00:09:33](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h09m33s)

Within your controller:

1. Check that the item is **saved** (`$data->id > 0`).
2. Verify necessary fields are set (e.g., `$data->name`).
3. Only then call a custom model method.

Example:

```php
if ($data->id > 0 && !empty($data->name)) {
    $model->performWork($data);
} else {
    $this->setMessage('Missing required data', 'error');
}
```

---

## 8. Handling Logic in the Model

[00:10:39](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h10m39s)

Inside the model:

```php
public function performWork($data)
{
    // Perform logic and return success or failure
    if ($this->save($data)) {
        return true;
    }
    return false;
}
```

Return `true` or `false` to trigger Joomla messages in the controller.

> **Best practice:** Use Joomla's `enqueueMessage()` to show feedback to users.

---

## 9. Compiling and Testing

[00:13:08](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h13m08s)

1. Save your Admin View in JCB.
2. Compile and install the component.
3. Test:

   * **List View:** "Test" button redirects correctly.
   * **Edit View:** "Work" button triggers your model method.
4. Inspect the generated files:

   * `controllers/looks.php` → list view controller
   * `controllers/look.php` → edit view controller
   * `models/look.php` → corresponding model

---

## 10. Adding the Same Button to Both List and Edit Views

[00:17:29](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h17m29s)

You can assign a button to appear in **both** areas:

1. Edit your button in JCB.
2. Change **Target View Type** to `Both`.
3. Save and compile again.

After installation:

* The button appears in both views.
* JCB automatically adds the necessary code to `view.html.php` in the toolbar generation method.

---

## 11. Permissions Integration

[00:19:43](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h19m43s)

JCB integrates permission checks automatically.
Each custom button has an **ACL switch** that respects Joomla's permission settings.

If a user lacks permission:

* The button is hidden from the toolbar.
* Even direct URL execution is blocked at the controller level.

> Always use Joomla's ACL check:

```php
if (!JFactory::getUser()->authorise('core.edit', 'com_demo'))
{
    throw new Exception('Not permitted', 403);
}
```

---

## 12. Summary and Best Practices

[00:20:53](https://www.youtube.com/watch?v=VyBxWpJWb40&t=00h20m53s)

You have now learned how to:

* Add **custom buttons** to list and edit views in JCB.
* Define **controller and model logic** for them.
* Manage **permissions** securely.
* Reuse this feature for automations, validations, and shortcuts.

> **Tip:**
> Experiment with different button types and methods - JCB handles the Joomla MVC integration, letting you focus purely on your custom logic.

---

### Key Takeaways

| Step | Description                                 |
| ---- | ------------------------------------------- |
| 1    | Choose your target view and button behavior |
| 2    | Define the controller method in JCB         |
| 3    | Add logic inside the controller and model   |
| 4    | Compile and test in Joomla                  |
| 5    | Implement permission checks                 |

---
