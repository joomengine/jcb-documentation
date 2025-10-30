# **Component Scripts - Joomla Component Builder Tutorial**

[Watch the video on YouTube](https://www.youtube.com/watch?v=xY9TWQrF8AQ&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Click on any timestamp below to jump to that moment in the video.*)

---

## **Overview**

In this tutorial, we explore the **Scripts tab** in **Joomla Component Builder (JCB)**.
This section enables developers to add **custom global scripting** to their components - including helper methods, CSS, JavaScript libraries, MySQL dumps, and dashboard data integration.

These options empower you to extend your component's functionality **without modifying the core JCB logic**, allowing better control and maintainability.

---

## **1. The Scripts Tab Overview**

[00:00:00](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h00m00s)

The **Scripts Tab** in JCB allows you to integrate custom scripting into your component in a **global or per-view** scope.
Here you can:

* Add PHP helper methods.
* Load CSS and JavaScript libraries (like UIKit or FooTable).
* Include global CSS or admin events.
* Add MySQL dumps.
* Create dashboard methods to dynamically populate backend data.

This tab is designed primarily for developers who wish to inject logic directly into the component.

---

## **2. Create User Helper Method**

[00:00:47](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h00m47s)

The **User Helper Method** allows you to write **custom PHP functions** that extend your component's functionality.

> **Note:**
> This feature is for developers comfortable with PHP.
> JCB will not generate logic automatically - you'll need to script it.

### **Example: Creating a User Automatically**

[00:01:29](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h01m29s)

Using the **Cost-Benefit Projection Tool** as an example:

* In the "Company" admin view, when adding a new company, if a user isn't selected but an email is entered, the component can **automatically create a Joomla user**.
* The helper method defines how this user is created and linked.

This behavior is triggered inside the controller's `postSaveHook()` method.

---

### **Locating the PostSaveHook**

[00:02:38](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h02m38s)

In the component's admin view:

1. Go to **Admin View → PHP tab**.
2. Locate the `postSaveHook` method.
3. This is where you can execute custom logic after a record is saved.

Within the method:

```php
if (!$userExists) {
    $userId = [[[Component]]]Helper::create_user($validData);
}
```

* The `[[[Component]]]` placeholder will be replaced by your component's codename.
* The helper method `create_user` is defined in your component's helper class.

---

### **Helper Class Implementation**

[00:04:13](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h04m13s)

Inside the helper class (e.g., `costbenefitprojectionHelper`), create your helper function:

```php
public static function create_user($validData)
{
    // Generate password if none provided
    if (empty($validData['password'])) {
        $validData['password'] = self::randomString();
    }

    // Create Joomla user
    $user = new JUser;
    if (!$user->bind($validData)) {
        return false;
    }

    $user->save();
    return $user->id;
}
```

This method:

* Generates a password if none exists.
* Creates and saves the Joomla user.
* Returns the new user's ID.

[00:06:41](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h06m41s)

After saving, the ID is stored in the company record, linking the user and company automatically.

---

## **3. Add UIKit and FooTable Libraries**

[00:07:01](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h07m01s)

You can enable popular CSS/JS frameworks with a toggle:

* **UIKit**: Adds responsive UI components automatically.
* **FooTable**: Enables dynamic tables.

These libraries are automatically included in your media folder and linked in your component.

> **Tip:**
> You don't need to manually enqueue them - JCB handles that dynamically.

---

## **4. Add Global CSS for the Admin Backend**

[00:07:32](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h07m32s)

If you want to style your admin interface globally:

* Add your CSS inside this section.
* It will apply to **all admin views** of your component.

Example:

```css
.icon-48-dashboard {
    color: #4CAF50;
}
```

---

## **5. Add Custom PHP Helper Admin Class**

[00:07:46](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h07m46s)

This field lets you inject custom PHP code into your **Helper_Admin class**, such as:

* Custom admin utilities
* Event triggers
* Helper functions for backend scripts

---

## **6. Add Global Admin Event**

[00:08:03](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h08m03s)

The **Global Admin Event** switch lets you add functions that execute **on every backend page load**.

When enabled:

* JCB triggers a predefined global event function.
* You can place any repetitive admin task inside it.

Example:

```php
public static function loadDropboxAjax($doc)
{
    $script = "console.log('Dropbox Ajax Loaded');";
    $doc->addScriptDeclaration($script);
}
```

This will inject the script globally across backend views.

[00:10:59](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h10m59s)

This is ideal for automation tasks such as syncing data, checking Dropbox updates, or loading assets dynamically.

---

## **7. Add Custom PHP Helper Site View**

[00:11:44](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h11m44s)

Front-end helpers differ from admin ones for **security and access control**.
You can add front-end specific helper methods, ensuring only safe logic runs publicly.

Example use:

* Syncing user data.
* Running Ajax updates securely on the front end.

---

## **8. Add MySQL Dump**

[00:13:49](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h13m49s)

You can import **SQL dump files** here rather than per view.
This is useful for:

* Preloading tables.
* Adding default data on installation.

> **Note:**
> Avoid adding the same SQL twice; JCB merges all dumps into a single installation file.

---

## **9. Dashboard Methods**

[00:14:23](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h14m23s)

**Dashboard Methods** let you show dynamic data directly on the component's backend dashboard - no extra view needed.

Example: Display usage statistics.

```php
public function getUsageData()
{
    // Custom data logic
    return $this->calculateUsage();
}
```

Convention:

* Methods starting with `get` automatically become available as `$this->usagedata`.
* The "get" prefix is dropped, and the remaining part is made lowercase.

So `getUsageData()` → `$this->usagedata`.

You can reference it in HTML like:

```php
<?php if ($this->usagedata): ?>
  <table>
    <!-- display data -->
  </table>
<?php endif; ?>
```

---

## **10. Adding Data to a Page**

[00:18:06](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h18m06s)

You can use dashboard methods to prepare and pass data to the view:

* Return arrays or objects.
* Loop through them in HTML templates.

Alternatively, you can use simple PHP or even just HTML for static dashboard elements, such as:

* Developer notes.
* RSS feeds.
* Component info.

[00:20:34](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h20m34s)

Example:

```php
<?php echo $this->rssfeed; ?>
```

---

## **Conclusion**

[00:21:27](https://www.youtube.com/watch?v=xY9TWQrF8AQ&t=00h21m27s)

The **Scripts Tab** provides advanced developers with a flexible framework to:

* Add logic beyond the auto-generated code.
* Extend helpers and controllers.
* Load dynamic data and styling.
* Automate tasks through global events.

If used wisely, it turns JCB into a **powerful rapid application framework** capable of handling sophisticated custom logic seamlessly within Joomla.

---

### **Summary of Key Script Areas**

| Feature            | Purpose                              |
| ------------------ | ------------------------------------ |
| User Helper        | Automate user-related actions        |
| UIKit/FooTable     | Add front-end UI libraries           |
| Global CSS         | Style all admin pages                |
| Helper Admin/Site  | Extend logic for backend or frontend |
| Global Admin Event | Run scripts across backend pages     |
| MySQL Dump         | Load default data                    |
| Dashboard Methods  | Display dynamic data in admin panel  |
