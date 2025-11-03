# Joomla Component Builder - Beginner-Friendly Guide

This guide provides a practical, beginner-friendly overview of how to use **Joomla Component Builder (JCB)** based on the *Introduction to Joomla Component Builder* tutorial.
It explains the essential workflow, tools, and best practices - with accurate, up-to-date details reflecting the latest JCB UI and behavior.

---

## 1) Prerequisites & Mindset

[00:00:18](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m18s)

JCB is designed for developers familiar with **PHP** and the **Joomla MVC framework**.

* **PHP knowledge:** The builder automates large parts of code generation but expects that you can understand and edit PHP.
* **Learning Joomla's API:** Explore Joomla's core structure (models, views, controllers) to understand how JCB-generated components fit in. Open the Joomla `/components` directory, browse its folders, and inspect how core components are structured.
* **Using an IDE (e.g., NetBeans):** You can jump to function definitions (like `getLayout`) to trace how Joomla handles rendering.

*Tip:* If you're new to PHP or Joomla MVC, consider online developer courses before diving deeper.

---

## 2) Local Development Environment

[00:04:17](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m17s)

You should **build and test components offline** on a local sandbox environment.

### Recommended Setup

* **Operating System:** Ubuntu or another Linux distribution.
* **Stack:** PHP, MySQL/MariaDB, and Joomla installed locally.
* **Debug Tools:** Add tools like Xdebug to inspect and debug your code efficiently.

Developing locally lets you work offline, debug easily, and avoid server-related issues.

*Resource Suggestion:* The course *"Up and Running with Linux for PHP Developers with Jon Peck"* (Lynda.com) is a great starting point for setting up your environment.

---

## 3) Security and Offline Preference

[00:07:51](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m51s)

Although JCB can run on a live server, it's best used **offline**.

When compiling, JCB places your build temporarily in the Joomla `/tmp` directory.
If hosted online, this could expose your compiled packages publicly.

To stay safe:

* Always develop locally when possible.
* If you must work online, delete temporary builds immediately after compiling.
* Limit server permissions to protect sensitive directories.

---

## 4) Understanding the Purpose of JCB

[00:03:55](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m55s)

The **Joomla Component Builder** was created to **accelerate development** by automating repetitive code generation for Joomla components.

It:

* Follows **Joomla conventions** closely.
* Lets you **customize generated code** freely.
* Supports **complex admin and site interfaces** using standard MVC structure.

You're encouraged to suggest improvements or share better implementation methods with the developer community.

---

## 5) Creating Your First Component

[00:05:43](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

Once JCB is installed in your local Joomla site:

1. Go to **Components → Component Builder → Components → New**.
2. Enter:

   * **Name:** The readable name of your component.
   * **Option:** Usually formatted as `com_example`.
   * **Description:** Short overview of purpose.
   * **Version:** Your current version number.
3. Save the new component.

You now have the foundation for your custom extension.

---

## 6) Adding Admin Views and Fields

[00:06:07](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m07s)

Admin views define the **backend structure** and determine how data is managed.

### Steps to Add an Admin View:

1. Navigate to **Admin Views → New**.
2. Choose between:

   * **Item View** (single record)
   * **List View** (multiple records)
3. Link the view to a **database table** (JCB auto-generates this table).
4. Configure ACL (permissions), toolbar options, and category/tag support.

### Adding Fields:

* Go to **Fields → New**.
* Define field type (text, list, media, repeatable, etc.).
* Assign the field to the correct admin view.
* Configure validation rules, default values, and filters.

Fields can be reused across views, plugins, and modules.

---

## 7) Building Frontend (Site) Views

[00:07:24](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m24s)

Frontend or "site" views define what visitors see on your website.

### Steps:

1. Go to **Site Views → New**.
2. Choose between **List** or **Item** view types.
3. Connect the site view to its corresponding table or Dynamic GET.
4. Define templates and layouts to control how data is displayed.

Templates allow page-level customization, while layouts define smaller view sections.

---

## 8) Using Dynamic GETs

[00:08:14](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m14s)

**Dynamic GETs** are JCB's **visual query builder**, letting you create advanced database queries without manual SQL.

Use a Dynamic GET when:

* You need to fetch data from multiple tables.
* You want to apply filters, joins, or ordering visually.

### To Create a Dynamic GET:

1. Go to **Dynamic GETs → New**.
2. Select a **base table**.
3. Add **joins**, **fields**, and **filters**.
4. Save it and link it to a **Site View** or **Admin Report View**.

This feature keeps your logic organized and reusable across multiple layouts.

---

## 9) Compiling and Installing the Component

[00:08:51](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m51s)

After defining views, fields, and templates, it's time to build your installable component.

### Compile Steps:

1. From the **Component list**, click **Compile**.
2. Choose:

   * **Test Mode (Dry Run):** Generate code without installation.
   * **Normal Build:** Create an installable ZIP file.
3. After successful build:

   * You can **install directly** from JCB's compiler view, or
   * Upload the ZIP via Joomla's **Extensions → Install**.

Verify that:

* Backend views load correctly under **Components → Your Component**.
* Site menu items link to frontend views as expected.

---

## 10) Contributing and Feature Requests

[00:09:50](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m50s)

The developer encourages collaboration to ensure JCB's ongoing improvement.

If you encounter issues or have feature suggestions:

* Report them publicly on GitHub under the **Issues** section.
* Start new **feature requests** there.
* For sponsored development or priority requests, you can reach out directly to the maintainer.

Engaging publicly ensures that discussions and resolutions benefit everyone.

---

## 11) Supporting the Project

[00:08:51](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m51s)

Since JCB is free, users are asked **not to distribute the training videos** without permission.
If you find value in the tool and it saves you time, consider contributing financially to help fund continued development.

Your support helps sustain improvements for the whole Joomla developer community.

---

## 12) Summary - Complete Workflow

[00:11:09](https://www.youtube.com/watch?v=9evJkBTnKxE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m09s)

1. **Set up** a local Joomla environment.
2. **Install** Joomla Component Builder.
3. **Create** your component (base configuration).
4. **Add** Admin Views and Fields.
5. **Build** Site Views and Templates.
6. **Use Dynamic GETs** for complex queries.
7. **Compile and Test** using Dry Run mode.
8. **Install** and verify functionality.
9. **Refine and iterate** until stable.
10. **Contribute** to the JCB community.

---
