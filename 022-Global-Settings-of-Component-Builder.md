# Global Settings of Joomla Component Builder (JCB)

The **Global Settings** panel in Joomla Component Builder provides the essential tools for configuring how your component behaves, manages records, handles permissions, and secures data.
Access to these settings is available through the **Options** button in the Component Builder dashboard.

---

## 1. Accessing Global Configurations

[00:00:00](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h00m00s)

1. Open the **Component Builder Dashboard**.
2. Click the **Options** button in the top toolbar.
3. The **Global Configurations** window will open.

Only users with proper permissions (usually Super Users or Administrators) can view and modify these options.
If the "Options" button is missing, adjust your Joomla user group permissions.

Inside the configuration window, you'll find several key tabs:

* **Global**
* **UiKit Settings**
* **Encryption Settings**
* **Folder Paths**
* **Permissions**

---

## 2. Check-in Timer

[00:01:16](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h01m16s)

The **Check-in Timer** determines how long an item remains locked when a user checks it out for editing.
Once the selected time passes, JCB automatically checks the item back in.

**Available intervals:**

* 5 hours
* 12 hours
* 24 hours
* Every second day
* Once a week
* Never

A 24-hour interval is generally recommended for most development workflows.

---

## 3. Enable Versioning

[00:01:55](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h01m55s)

Versioning allows JCB to track and store different versions of a record.

* **Yes** - Enables versioning.
* **No** - Disables versioning.
* **Number of Versions to Keep** - Set a maximum number of versions (enter `0` to keep all).

If your component is used frequently or stores large amounts of data, limiting stored versions helps maintain database performance.

---

## 4. Minify JavaScript (JS)

[00:02:25](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h02m25s)

JCB can automatically compress and minify all JavaScript files during the component's compilation.

* **Yes** - Minify JS files (recommended for production environments).
* **No** - Keep JS files unminified (recommended for development).

When minification is active, all JS assets in your compiled component are optimized to improve loading performance.

---

## 5. Contributor Information

[00:03:28](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h03m28s)

In this section, you can add the names of developers or contributors who worked on the component.
These names will appear under the **Contributors** section of the JCB dashboard.

This feature helps in maintaining proper credit and tracking development collaboration within teams.

---

## 6. UiKit Settings

[00:03:37](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h03m37s)

UiKit is a front-end framework that JCB optionally supports in both backend and frontend development.

Currently, UiKit is primarily implemented in limited backend areas.
It is intended for potential future use in JCB's frontend component structure (for example, when building frontend interfaces or dashboards).

You can safely leave these settings unchanged unless you are specifically working with UiKit-based front-end functionality.

---

## 7. Encryption Settings

[00:04:44](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h04m44s)

Component Builder includes data encryption features that protect sensitive information stored in the database.

To enable encryption:

1. Enter a **Basic Encryption Key** in the field provided.
2. Save the configuration.

Important notes:

* Once you set the key, do **not change or delete** it.
* If the key is removed, encrypted data will become permanently inaccessible.
* Always store this key securely in an offline or backup location.

This feature enhances the overall security of your component's stored data.

---

## 8. Folder Paths

[00:05:42](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h05m42s)

Folder paths allow JCB to know where to store backup and compiler files used during component development.

Currently, only the following folder paths should be used:

* **Backup Folder Path**
* **Git Folder Path**

The **Custom Folder Path** and **Compiler Folder Path** fields are placeholders for future development and should remain empty or unchanged.
These are designed for moving compiler-related folders outside of the web-accessible directory to improve security, though this feature is not yet fully implemented.

---

## 9. Permissions

[00:06:50](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h06m50s)

JCB integrates with Joomla's Access Control List (ACL) system, providing extensive permission management for your components.

Modern Joomla versions (3.5 and later) introduced Ajax-based saving, which allows JCB to update permissions without needing to reload the page or save the full configuration manually.

### Available Global Permissions

* Create
* Delete
* Edit
* Edit State
* Edit Own
* Edit Created By
* Edit Created Date

You can also configure per-view permissions for:

* Admin views
* Custom admin views
* Dynamic get views

If needed, assign specific groups the **Configure Options Only** permission, allowing them to manage configuration settings without full access to the component.

---

## 10. Example: Preacher Permissions

[00:10:05](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h10m05s)

The **Preacher** view in the *Sermon Distributor* component is an example of how JCB's permission structures operate.

In JCB, you can define whether permissions use:

* `view.edit` - to create view-specific control (e.g., `preacher.edit`)
* `core.edit` - to apply Joomla's global edit/delete rules

After compiling and installing the component, open **Options → Permissions** in Joomla to confirm that these new permission rules appear for the relevant views.

---

## 11. Field Permission Switch

[00:12:30](https://www.youtube.com/watch?v=LA2WDi8G79E&t=00h12m30s)

Field-level permissions provide precise control over who can modify individual fields.

To enable field-level control:

1. Go to the **Fields** tab in your component.
2. Select a specific field (for example, *Preacher Name*).
3. Enable **Permissions Switch**.
4. Save and close.
5. Recompile and install the component.

After installation, a new permission entry appears in Joomla's **Permissions** tab (e.g., *Preacher edit name*).
This allows you to grant or restrict edit rights to specific user groups.

To remove a field-level permission:

1. Return to the field in JCB.
2. Set **Permissions Switch** to **No**.
3. Recompile and reinstall the component.

Field permissions can be added or removed at any time and compiled into the component as needed.

---

## Summary

The **Global Settings** area of Joomla Component Builder provides developers with granular control over how components are configured, how users interact with them, and how securely they manage their data.

By understanding and properly configuring these options-especially versioning, encryption, and permissions-you can ensure that your components are secure, efficient, and professionally structured for any project environment.

---
