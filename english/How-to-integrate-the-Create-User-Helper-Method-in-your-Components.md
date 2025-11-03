# How to Integrate the Create User Helper Method in Your Components

**Tutorial Source:** [Joomla Component Builder Tutorial Series](https://www.youtube.com/watch?v=ckFakaQ90JY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
---

## 1. Overview

[00:00:00](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h00m00s)

The **Create User Helper Method** allows your Joomla Component to create Joomla Users dynamically from within your component views or actions. This is done using a built-in JCB Helper Class extension which adds reusable methods accessible across both front-end and back-end of your component.

This integration is helpful for components like job managers, membership systems, or expert directories-any place where a custom user creation process is needed.

---

## 2. Understanding the Helper Class

[00:00:32](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h00m32s)

Each JCB-generated component contains a **Helper Class**-one for the administrator side and one for the site side.

You can locate it in:

```
/administrator/components/com_expertdatabase/helpers/expertdatabase.php
```

This file defines the main `expertdatabaseHelper` class.
It is **automatically loaded** by Joomla every time your component runs, ensuring all helper functions are globally available.

[00:01:28](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h01m28s)

In the JCB admin interface:

1. Open **Component Builder Dashboard** → **Components** → select your component.
2. Scroll to **Library & Helpers**.
3. Locate the switch **Add Create User Helper Method** and toggle it **ON**.

[00:02:11](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h02m11s)

This command tells JCB to automatically include the "Create User" function in your helper class during compilation for both site and admin areas.

---

## 3. The Create User Function

[00:03:00](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h03m00s)

Once enabled, JCB adds a method like this to your helper class:

```php
public static function createUser($new)
```

You can call it using:

```php
expertdatabaseHelper::createUser($new);
```

Where `$new` is an **array** containing user registration data:

```php
$new = array(
    'username'  => 'testing123',
    'name'      => 'Testing 123',
    'email'     => 'testing123@vdm.io',
    'password'  => 'mySecretPass',
    'password2' => 'mySecretPass'
);
```

[00:03:26](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h03m26s)

The helper method leverages Joomla's built-in **User Registration Model**, creating the user via the standard Joomla API.

It simplifies the process but **does not automatically assign users to groups**-that must be handled manually after creation.

---

## 4. Using the Create User Function in a View

[00:04:30](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h04m30s)

Let's use the **Experts** admin view as an example.

When creating a new Expert:

1. Navigate to **Expert Database → Experts → New**.
2. You'll find a field labeled **Expert**, which allows you to select users within a specific group.
3. Below it, a **Create User** button appears.

[00:05:26](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h05m26s)

This opens a modal window where you can enter:

* Username
* Name
* Email
* Password

After submission, Joomla sends a success message confirming that the new user was created and login details were emailed.

[00:06:05](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h06m05s)

Once created, the new user becomes selectable from the user list field in the Expert form.

> **Tip:** Joomla usernames typically cannot contain numbers unless specifically allowed in your configuration or overridden via plugin.

---

## 5. Integrating Create User via AJAX

[00:09:30](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h09m30s)

To create users dynamically without reloading the page, JCB supports **AJAX integration**.

In JCB, an AJAX handler consists of:

* **Controller:** `/controllers/ajax.json.php`
* **Model:** `/models/ajax.php`

[00:10:04](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h10m04s)

The controller registers and executes AJAX tasks.
The model defines the corresponding methods such as:

```php
public function createUser()
{
    // custom logic using expertdatabaseHelper::createUser()
}
```

[00:11:31](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h11m31s)

These methods:

* Retrieve form data using Joomla's input filter.
* Validate and sanitize values.
* Call the Helper method to create the user.

JCB allows you to define these tasks directly in the component builder interface under **Ajax Methods**, mapping them to your PHP functions.

---

## 6. Global Helper Integration

[00:13:17](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h13m17s)

The Global Helper Class in JCB provides reusable functions like `createUser()`, `addToGroup()`, or `getUserField()`.
If you improve any of these functions, you can **fork the JCB project on GitHub** and submit a pull request.

[00:14:17](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h14m17s)

> **Note:** The `createUser()` method **does not** automatically add users to a Joomla User Group.
> You'll need to handle that logic in your component or through post-creation hooks.

---

## 7. Retrieving and Displaying User Data

[00:14:53](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h14m53s)

When the page loads, a `getUser` method may retrieve user data using AJAX.
The PHP backend fetches the user record and returns it as a JSON-encoded response.

[00:15:51](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h15m51s)

In JavaScript:

```javascript
$.ajax({
    url: 'index.php?option=com_expertdatabase&task=ajax.getUser&format=json',
    data: { user_id: selectedUserId },
    success: function(response) {
        // Populate the user data into the view
    }
});
```

This allows you to dynamically load, update, and display user info without refreshing the page.

---

## 8. Using Tokens for Security

[00:18:01](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h18m01s)

Always include a **CSRF Token** in every AJAX or form request to prevent cross-site scripting (XSS) attacks.

### In PHP:

```php
echo JHtml::_('form.token');
```

### In JavaScript (front-end calls):

```javascript
data[ '<?php echo JSession::getFormToken(); ?>' ] = 1;
```

[00:18:28](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h18m28s)

Tokens are automatically handled in the admin area but must be manually added on the front-end.

---

## 9. Extending or Modifying the Create User Helper

[00:20:20](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h20m20s)

If you need to modify the implementation:

1. **Fork JCB** on GitHub.
2. Locate the **Compiler files** under:

   ```
   administrator/components/com_componentbuilder/helpers/compiler/
   ```
3. Search for the function `createUser`.
4. Modify its logic to fit your needs.

[00:21:38](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h21m38s)

Because these helper methods are dynamically generated during compilation, you must edit the compiler logic rather than modifying compiled component code directly.

---

## 10. Summary

Integrating the **Create User Helper Method** in JCB:

1. Enable the helper in the **Component > Library & Helpers** area.
2. Use `yourComponentHelper::createUser($new)` to programmatically create Joomla users.
3. For dynamic interaction, use **AJAX models** and **controllers**.
4. Always include **CSRF tokens** for security.
5. Extend or customize via **Compiler files** for permanent modifications.

---

### Final Note

[00:19:41](https://www.youtube.com/watch?v=ckFakaQ90JY&t=00h19m41s)

This feature demonstrates the power of Joomla Component Builder as a **developer tool**, not just a UI generator.
It empowers you to integrate dynamic, secure user creation logic directly into your components.

---
