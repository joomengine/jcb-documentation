# **Setting Site View Permission in Joomla Component Builder**

> Video: *Setting Site View Permission* [00:00:00](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h00m00s)
> *(Click timestamps to view specific parts of the video)*

---

## **1. Overview**

[00:00:00](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h00m00s)

In Joomla Component Builder (JCB), **Site View Permissions** control front-end access for each view in your component. Those access gates also decide which plugin events can run, because a blocked view never reaches the point where Joomla fires site-level triggers. Cross-reference the [JCB! Joomla Plugins](./Joomla-Plugins.md) guide when auditing permissions so that automation and UI exposure remain aligned.
By default, these permissions are set to **"Not Allowed"**, because JCB relies on Joomla's **Global Component Permissions**. Unless these are explicitly written to the database (either manually or via script), no site view will be accessible on the front end.

---

## **2. Example: Using the Sermon Distributor Demo**

[00:00:49](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h00m49s)

This tutorial uses the **Sermon Distributor** demo component (available as a JCB example).
In this component:

* Navigate to **Options → Permissions**.
* Search for terms like **"Site"** to locate related permissions.

You'll find entries such as:

* `categories site access` (plural)
* `category site access` (singular)
* `preachers`, `series`, `sermons`, etc.

Each of these determines whether a specific view is publicly accessible.
By default, their values are **"Inherit"**, which shows as **"Not Allowed"** unless set globally.

> **Tip:** This default behavior prevents unauthorized front-end access until explicit permission is granted.

---

## **3. Defining a Default Site View**

[00:02:02](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h02m02s)

To improve user experience when permission issues arise, JCB provides a **Default View** mechanism.

### **Steps to Configure a Default View**

1. Open **Component Builder → Components → [Your Component] → Settings → Site Views.**
2. Add or edit a view.
3. Enable the **Default View** checkbox.

[00:02:40](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h02m40s)

The **Default View** acts as a fallback page when users try to access a restricted page.
It should typically be an **unrestricted page** that explains how users can gain access (e.g., by logging in or upgrading permissions).

[00:03:12](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h03m12s)

* Only **one** default view can exist.
* If multiple are marked, JCB will use the **first** one encountered during compilation.

[00:03:52](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h03m52s)

When a restricted page is accessed, JCB automatically **redirects** the user to this default view-avoiding endless loops or 403 errors.

> **Note:**
> This feature prevents access errors but doesn't replace Joomla's permission logic-it's a graceful fallback mechanism.

---

## **4. Adding Custom Post-Installation Scripts**

[00:04:48](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h04m48s)

You can automatically guide administrators to set permissions properly using **custom PHP post-installation scripts**.

### **Example: Add a Post-Flight Message**

In the **PHP (Post-Flight)** section of your component's *Install Script*:

```php
$app = \Joomla\CMS\Factory::getApplication();
$app->enqueueMessage(
    'First set the component global settings and permissions in the Options area. 
    The front end will not work as expected until each Site View has the correct access permissions.'
);
```

[00:05:54](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h05m54s)

You may also:

* Turn the message into a **link** directing to the Options page.
* Add logic to **update permissions automatically** after installation.

> **Advanced Option:**
> Use scripting here to pre-set public access for site views if your component requires immediate front-end availability.

---

## **5. Understanding Site Root Behavior in Code**

[00:06:38](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h06m38s)

Within the generated component code, JCB checks site view permissions using the **access file** (e.g., `access.xml`).

When a restricted view is accessed:

1. JCB checks if the user has permission.
2. If not, it **redirects** the user to the **default view**.
3. If the default view is not accessible (not the site root), JCB redirects to the **site's homepage**.

[00:07:32](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h07m32s)

This ensures that front-end permission conflicts never crash or loop the site.

> **Example:**
> Access denied on `/category` view → Redirects to `/preachers` (default) → If `/preachers` not accessible → Redirects to homepage.

---

## **6. Example of Permission Error Handling**

[00:08:57](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h08m57s)

If a user lacks permission, JCB will show a localized error, such as:

```
COM_SERMONDISTRIBUTOR_NOT_AUTHORISED_TO_VIEW_CATEGORIES
```

You can customize this message or even add logic to display a prompt (e.g., *"Please log in or purchase access to view this section."*).

> **Improvement Idea:**
> Add a field in your component that allows admin users to set a **custom message** for unauthorized access.

---

## **7. Using Custom Code Implementations**

[00:09:35](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h09m35s)

JCB supports **Custom Code Implementations**, allowing you to override generated code at compile time.

Use this to:

* Insert custom access logic.
* Change redirection behavior.
* Modify permission-related messages.

[00:10:10](https://www.youtube.com/watch?v=gWjQjdhYqXI&t=00h10m10s)

For more detailed customization examples, see JCB's dedicated tutorial on **Custom Code Implementation**.

---

## **8. Summary**

| Feature                 | Description                                  |
| ----------------------- | -------------------------------------------- |
| **Default Permission**  | "Not Allowed" unless explicitly granted      |
| **Default View**        | Redirect fallback for unauthorized access    |
| **Post-Install Script** | Displays setup reminders or auto-sets access |
| **Code-Level Control**  | Redirects to safe views or homepage          |
| **Custom Code**         | Modify or extend access control logic        |

---

## **Best Practices**

* Always define a **Default View** to prevent redirect loops.
* Use **Custom Post-Flight scripts** to remind or enforce permission settings.
* Customize error messages for better UX.
* Use **Custom Code Implementations** for complex access logic.
* Test your compiled component's front-end behavior after installation.

---
