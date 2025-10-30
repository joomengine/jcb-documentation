# Setup Site Edit View in Joomla Component Builder

Learn how to configure and enable editing for an **Admin View** on the **front-end site** using Joomla Component Builder (JCB). This allows users to **create** and **edit** component items directly from the public interface - with permissions controlling who can do what.

---

## 1. Add Admin View to the Front-End Site

[00:00:00](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h00m00s)

JCB enables linking an **Admin View** (the backend editing interface) to the **front-end** of your Joomla website so that users can edit or submit data from the site.

1. **Compile and install** your component using JCB's compiler.
2. Open your installed component in Joomla.
3. In this example, the **Demo Component** contains an Admin View called **"Looks"**.
4. If you open the *List View* for "Looks", you'll find fields such as:

   * Email
   * Mobile phone
   * Date of birth
   * Image
   * Website
   * Publishing, Permissions, and Structure settings

These fields collectively form what JCB calls an **Admin View** - a structure defining how records are created and edited in your component.

---

## 2. Add Editing Area to the Front-End

[00:01:50](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h01m50s)

To make the Admin View editable from the site front-end:

1. Go to the **Permissions tab** in your component's view configuration.
2. You'll see controls for:

   * **Global permissions** (set in *Options*)
   * **Local permissions** (per view)

For example:

* If the public users should be able to **submit new items**, set **"Create"** to *Allow*.
* To let them **edit their own submissions**, also set **"Edit Own"** and **"Edit State"** to *Allow*.

> **Tip:** These permissions apply both globally and locally per view. Make sure both are configured correctly if edits are not visible on the site.

---

## 3. Understand the Two Permission Switches

[00:03:30](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h03m30s)

There are **two main permission switches** that determine front-end access:

1. **Global Switch:** Located under *Options* - controls access across the entire component.
2. **Local Switch:** Found in each Admin View - controls access for that specific view.

If a front-end edit form does not appear or fails to open, revisit these settings to ensure the appropriate user group (e.g., *Registered* or *Author*) has editing permissions.

---

## 4. Enable Site Edit View in Component Settings

[00:04:21](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h04m21s)

Now enable JCB to generate the code for the Site Edit View.

1. Open **JCB → Components** and select your component.

2. In the **Settings** tab, open the configuration that lists all linked Admin Views.

3. Ensure **"Edit/Create Site View"** is set to **Yes**.

   * This tells JCB to automatically generate a **Site View**, **Model**, and **Controller** for this Admin View.
   * The front-end form will then be available for editing or creating items.

4. Click **Save**, then **Save & Close**.

5. Re-compile your component and re-install it.

---

## 5. Inspect Generated Code: MVC Structure

[00:06:05](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h06m05s)

After compilation, check your Joomla installation:

* Navigate to `/components/com_yourcomponent/`
* You will find:

  * `/controllers/look.php`
  * `/models/look.php`
  * `/views/look/`

Each corresponds to the **Model-View-Controller** (MVC) files that JCB created.

The generated code is similar to the backend but adapted for the front-end. It includes necessary scripts, form handling, and layout adjustments suitable for site users.

> **Note:** Although the code is created, JCB does not automatically generate menu links or buttons to access these front-end forms. These need to be added manually.

---

## 6. Add Manual Links to the Front-End

[00:07:51](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h07m51s)

To enable users to access and edit specific items from the site:

1. Go to **JCB → Site Views**.
2. You'll see:

   * `Looks` (list view)
   * `Looking` (possibly a related view)

Since the "Look" site edit view was auto-generated, you do not need to create it again. However, you must manually create **links** to it.

3. Open **Dynamic GETs** in JCB.
4. Locate the dynamic get entries for "Looks" and "Looking".
5. Edit the "Looks" Dynamic Get - in its **Custom Script** area, check for code that looks like this:

   ```php
   if ($cando->get('core.edit')) {
       $item->edit_link = '<a href="' . JRoute::_('index.php?option=com_demo&view=look&id=' . (int) $item->id) . '">Edit</a>';
   }
   ```

This snippet dynamically adds an **Edit button** for users who have permission.
The helper method `getAction()` determines whether the logged-in user can edit the specific item.

---

## 7. Add Button to Create New Items

[00:11:19](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h11m19s)

To let users create new items from the front end:

1. Copy the edit button script used in the Dynamic Get.

2. Modify the link to point to **ID = 0** (new item):

   ```php
   <a href="index.php?option=com_demo&view=look&id=0">Create New Look</a>
   ```

3. Place this button before your list or table of items in the Site View.

This adds a "New Look" button that loads the front-end creation form.

---

## 8. Understand the Helper Class and Permissions Logic

[00:12:23](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h12m23s)

JCB automatically adds a helper file to your component, e.g.:

`/components/com_demo/helpers/demo.php`

In this file, locate the method:

```php
public static function getAction($itemId)
```

This method:

* Checks user permissions (`core.edit`, `core.edit.own`, `core.create`)
* Returns an object containing boolean values indicating what the user can do
* Is used by the dynamic get script to show or hide edit/create links

> **Tip:** You can use `var_dump($cando); exit;` to debug and inspect what actions are available to the logged-in user.

---

## 9. Verify and Adjust Permission Behavior

[00:14:33](https://www.youtube.com/watch?v=tmB22d9dQ4M&t=00h14m33s)

If front-end editing or creation does not work:

* Check the **Authorise** setting for your Site View ("Looks").
* Ensure the **Permissions structure** is correctly aligned with your component's logic.

Remember:

> JCB automatically injects a comprehensive permission structure into every Admin and Site View it generates. Always verify both **Global** and **Local** permissions before troubleshooting.

---

### Summary

By following these steps, you have:

* Enabled a Site Edit View for an Admin View ("Look")
* Allowed users to edit and create records on the front end
* Controlled access via JCB's built-in permission system
* Added manual links to handle "Edit" and "New" functionality
* Understood how `getAction()` manages permissions dynamically
