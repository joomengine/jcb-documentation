# Building a Hello World Component with Joomla Component Builder v2.6.0

*Based on tutorial: "Hello World Component with Joomla Component Builder Creator - Extended"* 
*(Updated for JCB v2.6.0)* 

---

## Overview

[00:00:00](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s) 
This guide explains how to create a **Hello World Component** using **Joomla Component Builder (JCB)** version **2.6.0**. 
JCB is a comprehensive framework for building Joomla components visually, automating repetitive code, and maintaining uniform conventions across projects.

---

## 1. Introduction to Joomla Component Builder

### Purpose

[00:00:41](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m41s) 
JCB automates the creation of Joomla components by compiling standardized, boilerplate structures into installable extensions. 
Changes made in the JCB compiler are instantly applied across all components.

### Key Concept

- Make **one change**, recompile, and apply it to all components.
- Maintain consistent **object-oriented conventions**.
- JCB automatically handles boilerplate code generation for Joomla components.

---

## 2. Requirements and Setup

### Prerequisites

[00:04:08](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s) 
- Basic knowledge of **PHP** and the **Joomla API**. 
- Familiarity with **database structures** (tables, fields, and relationships).

> **Tip:** If you're new to Joomla development, review Joomla's *Article Manager XML structures* for examples of database field mappings.

### Recommended Environment

[00:08:01](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m01s) 
- Install Joomla locally or on a private development server.
- Use an IDE (such as PhpStorm or VS Code) for editing JCB-generated code.

> A local setup makes it easier to extract custom code and re-import it during compilation.

---

## 3. Installing Joomla Component Builder

### Step 1: Access Joomla Admin

[00:09:56](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m56s) 
Navigate to **System → Manage → Install**.

### Step 2: Choose Installation Method

- **From Package:** Download JCB's `.zip` from GitHub or the official site. 
- **From URL:** Paste the GitHub repository URL. 
- **From Web:** Find "Component Builder" under *Tools → Developing Tools* and click **Install**.

> The JCB package is large; installation speed depends on your internet connection.

---

## 4. Understanding JCB's Structure

### Components, Admin Views, and Fields

[00:11:57](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m57s) 
To create a component:
1. Define **Field Types**.
2. Create **Fields** using those Field Types.
3. Create **Admin Views**, which act as database tables.
4. Link Admin Views to your **Component**.

**Relationships:**
- **Admin Views** → Database Tables 
- **Fields** → Database Columns 
- **Field Types** → XML field definitions

### Backend Before Frontend

[00:13:34](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m34s) 
Always build the backend (Admin Views and database structure) before creating frontend Site Views.

---

## 5. Creating Field Types

[00:14:15](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m15s) 
JCB comes preloaded with many **Field Types** (e.g., Text, Radio, Checkbox, Date, List). 
You can extend or modify them as Joomla evolves.

> **Note:** Joomla deprecated *Repeatable Fields*; use **Subform Fields** instead.

### Example: Adding a Custom Field Type

1. Go to **Fieldtypes → New**.
2. Define its **properties**:
   - Name 
   - Default value 
   - Adjustable / Mandatory / Translatable 
   - Description 

Example of XML definition inside a Field Type:

```xml
<field
    name="example_text"
    type="text"
    label="Example Text"
    description="Add your text here."
    required="true"
    default=""
/>
```

---

## 6. Creating Fields

[00:17:42](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m42s)
We'll create a **Text Field** named "Greetings".

### Steps

1. Go to **Fields → New**.
2. Select **Field Type: Text**.
3. Fill in details:

   * **Label:** `Greetings`
   * **Name:** `greeting`
   * **Hint:** `Add greeting here`
   * **Type:** Text
   * **Default:** (leave empty)
4. Save & Close.

---

## 7. Creating an Admin View

[00:24:46](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m46s)
Admin Views represent your backend database tables.

### Step-by-Step

1. Go to **Admin Views → New**.
2. **System Name:** `greetings_first`
3. **Single Record View:** `Greeting`
4. **List Record View:** `Greetings`
5. **Type:** `Read & Write`
6. **Short Description:** `Manages greetings records`
7. Save the view once (this creates the database structure).

### Linking Fields

[00:29:45](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m45s)

1. Open **Fields and Conditions** tab.
2. Click **Create Linked Fields** → Add the Fields you've created.
3. Configure field properties:

   * Show in Admin List View.
   * Order (e.g., "Name" first, "Greetings" second).
   * Set sortable, searchable, and linkable as needed.

Example configuration:

```json
{
  "field": "greetings",
  "list_order": 2,
  "sortable": true,
  "searchable": true,
  "linkable": false
}
```

Save and close the Admin View.

---

## 8. Creating the Component

[00:33:11](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h33m11s)
Now create the **Hello World Component**.

### Steps

1. Go to **Components → New**.
2. **System Name:** `hello_world_v2`
3. **Code Name:** `Hello World`
4. **Version:** `2.0.0`
5. Add company name, author, and description.
6. Save once.

### Link the Admin View

[00:34:01](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h34m01s)
In the component settings:

* Click **Create Component Admin View**.
* Select the previously created **Greetings** view.
* Choose an icon (Icomoon default) and assign it to the Main Menu.
* Enable "Add Record" on Dashboard.

Enable the following:

* Auto Check-in
* Keep History
* Has Metadata
* Access Control (Public / Registered / Special)

Save and close.

---

## 9. Compiling and Installing the Component

[00:43:04](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h43m04s)

1. Go to **Compiler**.
2. Select your component.
3. Click **Compile**.

JCB will generate:

* ~9,000 lines of PHP
* 51 folders
* 122 files

[00:44:17](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h44m17s)
Once compiled, click **Install on this Joomla site** or use the `.zip` package via Joomla's installer.

---

## 10. Adding Icons and Images

[00:44:42](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h44m42s)
If your component lacks an icon:

1. Edit the Admin View → assign icons for "List" and "Add".
2. Recompile and reinstall.

You'll now see the new icons in the Joomla admin.

---

## 11. Adding Dynamic GETs

[00:48:42](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h48m42s)
Dynamic GETs are queries that define what data is fetched from your component's database for frontend use.

### Create Two Dynamic GETs

* **ListGreetings:** returns all published greetings.
* **Greeting:** returns one greeting by ID.

Example configuration for **ListGreetings**:

```php
WHERE a.published = 1
ORDER BY a.ordering ASC
```

For **Greeting**, add:

```php
WHERE a.id = :id
```

and pass the ID via URL.

You can also join Joomla's user table:

```sql
JOIN #__users AS b ON a.created_by = b.id
```

Save both Dynamic GETs.

---

## 12. Creating Site Views

### Site View 1: List View ("Greetings")

[00:58:30](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h58m30s)

1. Go to **Site Views → New**.
2. **System Name:** `greetings`
3. **Code Name:** `greetings`
4. **Main Get:** `ListGreetings`
5. Save.

#### Snippet Example

```php
<?php foreach ($this->items as $item) : ?>
    <p><?php echo $item->name; ?></p>
<?php endforeach; ?>
```

---

### Site View 2: Single View ("Greeted")

[01:23:56](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h23m56s)

1. Create another Site View called **Greeted**.
2. **Main Get:** `Greeting`
3. Add simple panel display.

Example:

```php
<div class="uk-panel">
  <h3><?php echo $this->item->name; ?></h3>
  <p><?php echo $this->item->greeting; ?></p>
</div>
```

Link both Site Views to the component under **Component → Site Views**.

---

## 13. Adding the Component to the Frontend Menu

[01:09:53](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h09m53s)

1. Create several greetings in the backend.
2. Go to **Menus → Main Menu → New Menu Item**.
3. Choose **Menu Type: Hello World → Greetings (site)**.
4. Save and close.

If "Page not redirecting properly" occurs, check the **Access Control** on the Site View:

* Ensure `Public` is selected.

---

## 14. Adding the Alias Field for SEO-Friendly URLs

[01:14:11](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h14m11s)

1. Go to the **Admin View** → click the **Linked Fields** icon.
2. Add the existing **Alias** field to the Greetings Admin View.
3. Save and close.

This creates slug-based URLs for each greeting.

---

## 15. Testing Data and Display

[01:20:46](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h20m46s)
Use a PHP var_dump in the site view to confirm:

```php
<?php var_dump($this->items); ?>
```

Recompile and reinstall. You'll see slugs for each item.

---

## 16. Linking Records Using Helper Route

[01:22:36](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h22m36s)
Each Site View has a helper route.
Use the following pattern to create links dynamically:

```php
<a href="<?php echo JRoute::_(
  Hello_worldHelperRoute::getGreetedRoute($item->slug)
); ?>">
  <?php echo $item->name; ?>
</a>
```

Compile and reinstall.

---

## 17. Managing Permissions

[01:41:03](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h41m03s)
Set permissions to control **Edit**, **Create**, and **View** access.

Go to:

* **Component Options → Permissions**
* Adjust per group:

  * `Greetings (site) access`
  * `Greeted (site) access`
  * `core.edit`
  * `core.create`

When permission is granted:

* Edit buttons appear.
* Create buttons are visible.
* Unauthorized users see access restriction messages.

Example PHP snippet for permission-controlled edit button:

```php
<?php if ($canDo->get('core.edit')) : ?>
  <a href="<?php echo $editLink; ?>">
    <i class="icon-pencil"></i>
  </a>
<?php endif; ?>
```

---

## 18. Editing and Creating Items from the Frontend

[01:34:52](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h34m52s)
Enable frontend editing:

1. Add PHP checks for user authority in your List and Single Site Views.
2. Insert an edit link icon if permissions allow.

Example snippet:

```php
<?php if ($this->user->authorise('core.edit', 'com_hello_world')) : ?>
  <a href="<?php echo $editLink; ?>"><i class="icon-pencil"></i></a>
<?php endif; ?>
```

Add "Create" button with similar permission checks.

---

## 19. Compile and Test Again

[01:43:17](https://www.youtube.com/watch?v=IQfsLYIeblk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=01h43m17s)
Recompile after each change and reinstall the component.
Test the following:

* View greetings list.
* Open a single greeting.
* Edit and create new greetings.
* Confirm that permissions behave as expected.

---
