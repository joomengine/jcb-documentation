# How to Set Up a Store Message Method Alongside the Email Helper Class

[00:00:00](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Click on timestamps to view the corresponding sections in the video.*)

---

## 1. Overview

In Joomla Component Builder (JCB), the **Email Helper Class** allows developers to send customized emails from their components. However, there are scenarios where you may want to **store the sent message** for record-keeping or advanced workflows.

This tutorial shows how to:

* Extend the Email Helper Class to include a **store message method**.
* Configure your component to record and manage outgoing messages.

---

## 2. Understanding the Email Helper Class

[00:00:24](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m24s)

The **Email Helper Class** is automatically placed inside your component's backend helper folder.
Its path follows this pattern:

```
administrator/components/com_[component_name]/helpers/email.php
```

For example, if your component is named **Jobtracking**, the helper class is:

```
administrator/components/com_jobtracking/helpers/email.php
```

To call the email helper in your **custom script**, use the three-bracket syntax:

```php
[[[component]]]email.send($data);
```

[00:00:59](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m59s)
This syntax instructs JCB to locate and execute the email helper class dynamically when compiling your component.

---

## 3. The "Send" Method and Its Role

[00:01:17](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m17s)

Inside the **Email Helper Class**, there is a `send()` method that manages the process of sending an email.
When the email is successfully sent, the result is stored in a variable such as `$sendEmail`.

[00:01:47](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m47s)
At the end of this method, JCB allows you to call another helper method-**if it exists**-to perform additional actions after the email is sent (like logging or storing).

This check is performed using:

```php
if (method_exists('JobtrackingHelper', 'storeMessage'))
```

This ensures the `storeMessage()` method is only called if it has been explicitly defined in your component's **Admin Helper**.

---

## 4. Adding the `storeMessage()` Method

[00:02:19](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m19s)

### Step 1: Access the Admin Helper in JCB

1. Open **Joomla Component Builder**.
2. Go to your component.
3. Navigate to **"Libs & Helpers"** in the left-hand menu.
4. Scroll down to **Add PHP (admin_helper)**.

[00:02:47](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m47s)

### Step 2: Create the `storeMessage()` Function

Add the following function inside the **Admin Helper** area:

```php
public static function storeMessage($subject = null, $body = null, $recipient = null, $headers = null, $attachments = null)
{
    // Example: Save email data to a custom database table or log file
}
```

### Step 3: Understand Parameter Defaults

[00:03:19](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m19s)

Each parameter in the function signature has a **default value of `= null`**, ensuring the method runs even if some arguments are not passed.

Typical parameters include:

* `$subject` - The subject line of the sent email.
* `$body` - The body content of the message.
* `$recipient` - The recipient's email address.
* `$headers` - Optional headers used in the email.
* `$attachments` - Any attached files.

You only need to handle the first **four values** in most cases.

---

## 5. Integrating the Method into Email Helper

[00:04:17](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m17s)

The Email Helper's `send()` method checks for the existence of `storeMessage()` and, if found, passes the relevant variables:

```php
if (method_exists('JobtrackingHelper', 'storeMessage')) {
    JobtrackingHelper::storeMessage($subject, $body, $recipient, $headers, $attachments);
}
```

[00:04:52](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m52s)
If the method **does not exist**, it simply skips this part and returns the `$sendEmail` result.
If it **does exist**, it executes the `storeMessage()` method-allowing you to handle or log email data dynamically.

---

## 6. Using User Information with `getVar()`

[00:05:09](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m09s)

To associate stored messages with specific Joomla users:

* Use the `getVar()` method from the **User Class**.
* Match the email recipient to the user's record and retrieve the user ID.

Example:

```php
$userId = JFactory::getUser()->getVar('id', 'email', $recipient);
```

Once you have the `$userId`, you can link the stored message to that user record in your database.

---

## 7. Storing the Message

[00:05:38](https://www.youtube.com/watch?v=peVNLsAncGY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m38s)

You can now:

* Store messages in a **custom database table** (e.g., `#__jobtracking_messages`).
* Include fields such as:

  * Message ID
  * User ID
  * Subject
  * Body
  * Date sent
  * Status (e.g., success/failure)

The `storeMessage()` method gives you complete control to:

* Record email logs.
* Manage delivery results.
* Extend component functionality beyond simple sending.

---

## 8. Summary and Best Practices

* Always **define `storeMessage()`** in your Admin Helper if you plan to track or store emails.
* Use **default parameter values (`= null`)** to prevent runtime errors.
* Employ the `method_exists()` check to ensure safe execution.
* Combine this approach with Joomla's native **logging or database storage** methods for reliability.
* Keep your code modular-avoid placing logic directly in the Email Helper.

---

## 9. Practical Use Case

A typical use case might be an automated **notification system**:

* When a user action triggers an email (e.g., job update or form submission),
* The message is sent using the Email Helper,
* Then stored via `storeMessage()` for audit tracking or later review.

---

**End of Tutorial**
**Video Reference:** [How to Setup a Store Message Method Alongside the Email Helper Class](https://www.youtube.com/watch?v=peVNLsAncGY)

---
