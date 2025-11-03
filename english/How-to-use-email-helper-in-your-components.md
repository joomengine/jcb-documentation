# How to Use the Email Helper in Your Components

**Tutorial Reference:** [Video - How to Use Email Helper in Your Components](https://www.youtube.com/watch?v=tp6mMUTOF2Y)

## 1. Introduction to the Email Helper Class

[00:00:00](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h00m00s)

The **Email Helper Class** in Joomla Component Builder (JCB) is a reusable class located in the **Helpers** section of a component. It enables developers to easily send emails from within any part of their component.

* The helper file is usually named `email.php`.
* It extends JCB's abstract helper class.
* It uses Joomla's built-in mailer (`JMail`) to prepare and send messages.

**How It Works:**
When an email is sent, the helper creates an instance of Joomla's mailer, loads the necessary variables, and sends the message with the proper configuration.

---

## 2. Setting Up the Email Helper Class

[00:01:02](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h01m02s)

1. From your **Component Builder Dashboard**, open your component (e.g., Learning Manager).
2. Go to **Libs & Helpers** under the editing section.
3. Turn **Add Email Helper** to **Yes**.

> **Note:**
> Enabling this adds the Email Helper class to your component, but it doesn't automatically implement email functionality. You'll still need to configure the related settings and fields.

---

## 3. Adding Mail Configuration Fields in Component Settings

[00:01:47](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h01m47s)

To customize your component's email settings, you must add **custom configuration fields**.

1. Go to your component's **Settings** > **Config Area**.
2. Click **Add Config Field**.
3. Scroll down to find the **Mail Configuration** section.
4. Recreate the mail-related fields similar to those in Joomla's Global Configuration (found in `configuration.xml`).

These include:

* Mailer Type (`mailer`)
* From Name
* From Email
* Reply-To Address
* SMTP Host, Port, Username, Password, etc.
* DKIM fields (optional but recommended)

> **Tip:**
> You can review Joomla's default configuration file to match field names correctly. The "name" attribute is the key identifier used in code.

---

## 4. Understanding Field Names in Code

[00:02:45](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h02m45s)

Each config field includes:

* **Name** - used in the code (e.g., `mailer`, `smtp_host`)
* **Label** - visible in the UI
* **Description** - explains the field's purpose

When writing code, ensure the **field name** matches exactly with what's declared in your component's XML.

---

## 5. Configuring the Component Mailer Options

[00:03:35](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h03m35s)

In your component's **Options** tab, you'll find a **Mail Configuration** section.
Here, you can:

* Enable/disable mailing via the **Mailer Switch** (`On` or `Off`)
* Override Joomla's global mail settings (if desired)
* Set DKIM configuration for email authentication

If you choose **Global**, the component will use Joomla's default mail settings.

---

## 6. Joomla Global Mail Settings

[00:04:10](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h04m10s)

If you haven't configured your component's mail fields, JCB will use the **Joomla Global Configuration → Server → Mail Settings**.

These include:

* Global mailer type
* From address and name
* SMTP settings
* DKIM configuration

Any component without its own mail setup will fall back to these Joomla-wide settings.

---

## 7. Component-Level Email Overrides

[00:05:08](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h05m08s)

When the **Global** option is turned **off**, your component can define its own mailer settings (SMTP credentials, mail type, etc.).
This is especially useful if your component should send emails through a different mail server.

---

## 8. DKIM Configuration and Encryption

[00:05:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h05m40s)

DKIM (DomainKeys Identified Mail) adds authentication to your emails, reducing spam risk.

To use DKIM:

1. Enable **Use DKIM** in your Mail Configuration.
2. Provide:

   * Private Key
   * Public Key
   * Selector
   * Domain

If DKIM is set to "Yes" but values are missing, it won't be applied.

> **Recommendation:**
> Review Joomla's `JMail` DKIM documentation for advanced implementation details.

---

## 9. How the Helper Works in Code

[00:07:15](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h07m15s)

Within your helper code, the mailer is obtained from the component's configuration.
If `mailer` is set to **global**, Joomla's configuration is used. Otherwise, the component's custom settings apply.

The **`send()`** method handles:

* Recipient setup
* Subject & body content
* Mailer configuration
* Error handling and logging

> **Performance Tip:**
> Although capable of sending multiple emails at once, always consider your server's limitations to avoid spam issues.

---

## 10. Handling DKIM and Mailer in Code

[00:08:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h08m40s)

The DKIM values are injected into the `$mailer` instance before sending.
JCB uses Joomla's extended `JMailer` class, allowing you to configure advanced mail options securely.

---

## 11. Error Checking and Message Storage

[00:09:12](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h09m12s)

The helper includes built-in error handling.
If sending fails, it checks whether your component's helper (`componentnamehelper.php`) has a **`storeMessage()`** method.

This custom method:

* Logs or stores messages sent through your component.
* Can also record successful messages for user access.

**Example Signature:**

```php
storeMessage($recipient, $subject, $body, $type = 'email')
```

This enables users to later view messages sent to them, creating a full audit trail within your component.

---

## 12. Implementing the Email Helper in a Component

[00:11:39](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h11m39s)

**Example:**
In the **Job Tracking System**, emails are sent when a **Job Order** is created.

1. Enable **Add Email Helper** in your component settings.
2. In your **Admin View**, add a **Send Email** button (e.g., in the Job Order form).
3. The button triggers the `sendEmail` task.

When the user clicks the button:

* The component sends the email to the client (e.g., `testing@vdm.io`).
* A confirmation message appears in the top-right corner.

---

## 13. Code-Level Implementation Example

[00:13:40](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h13m40s)

The **Job Order** admin view includes a JavaScript function that calls a PHP controller task:

### Frontend JavaScript

```javascript
function sendEmail() {
    Joomla.request({
        url: 'index.php?option=com_joborder&task=sendEmail',
        method: 'POST',
        data: { email: recipientEmail },
        onSuccess: function(response) {
            Joomla.renderMessages({ success: [response.message] });
        }
    });
}
```

### Controller (PHP)

```php
public function sendEmail()
{
    $model = $this->getModel('Ajax');
    $result = $model->sendEmail($this->input);
    echo json_encode($result);
    JFactory::getApplication()->close();
}
```

### Model Method

```php
public function sendEmail($input)
{
    $mail = Helper::get('email');
    $result = $mail->send($to, $subject, $body, true);
    return $result ? ['success' => true] : ['error' => 'Failed to send email'];
}
```

This flow:

1. JS triggers the Ajax request.
2. Controller handles the `sendEmail` task.
3. Model uses the **Email Helper** to send mail.

---

## 14. Final Notes

[00:17:43](https://www.youtube.com/watch?v=tp6mMUTOF2Y&t=00h17m43s)

The **Email Helper Class** simplifies sending mail within your component while maintaining flexibility and consistency with Joomla standards.

**Benefits:**

* Centralized mail logic
* Configurable DKIM and SMTP support
* Seamless integration with Joomla Global Config
* Extendable logging and message storage

---
