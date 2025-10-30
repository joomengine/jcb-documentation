# CUSTOM ADMIN VIEWS

and follow the existing documentation tone and layout you've used throughout your Joomla Component Builder (JCB) series.

Here's the final integrated, professionally formatted Markdown documentation for **Custom Admin Views** - complete with accurate workflow explanations, enhanced clarity, timestamps, and up-to-date Joomla Component Builder details.

---

# CUSTOM ADMIN VIEWS

[00:00:00](https://www.youtube.com/watch?v=gtdQ1lwB9ds&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Click on these time links to see YouTube video.*)

---

## Overview

Custom Admin Views in **Joomla Component Builder (JCB)** are specialized backend views that allow you to display **custom layouts, reports, dashboards, or analytics** within the Joomla administrator area.

While **Site Views** are focused on frontend presentation, **Custom Admin Views** allow you to build highly interactive, PHP-driven, and permission-controlled admin interfaces.

In this example, we'll reference the **Cost-Benefit Projection** component, which uses Custom Admin Views to visualize company health data and intervention impact.

---

## Example: Cost-Benefit Projection Component

[00:00:33](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h00m33s)

The Cost-Benefit Projection component is used to show companies the **cost benefits of addressing certain diseases or causes** within their workforce.

It has two key Custom Admin Views:

* **Company Results**
* **Combined Results**

These views display data accessible only to users with specific permissions.

[00:01:04](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h01m04s)

From the admin panel, under **Companies**, each company entry includes an icon to open its result data.
Additionally, there's a **"Combined Results"** button that dynamically appears - this is automatically created by JCB.

[00:01:36](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h01m36s)

---

## Component Builder Custom Admin View

[00:01:55](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h01m55s)

Inside JCB, a **Custom Admin View** represents a blank area where you can load **custom HTML, PHP, and JavaScript**.

Everything within the white workspace area is managed by you - including content rendering, button controls, and data visualization.

[00:02:07](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h02m07s)

You can add a sidebar menu and link this view to other areas of the component, such as company lists or dashboards.

Each view can be linked to a specific company or record. From there, clicking **Edit** will open the connected record for modification.

[00:03:10](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h03m10s)

If you close the edit window, JCB returns you to the same result page, ensuring smooth workflow continuity for the user.

[00:03:35](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h03m35s)

---

## Adding a Custom Admin View in JCB

To create a new Custom Admin View:

1. Open **Joomla Component Builder → Admin Views**.
2. Click **New → Custom Admin View**.
3. Enter the **Name** (e.g., `Company Results`).
4. Choose a **Menu Location** if you want it visible under a specific admin menu section.
5. Add **Custom Layout Code** in the editor area (PHP, HTML, or template calls).
6. Optionally link **fields**, **layouts**, or **template files**.
7. Save the view.

Once compiled, JCB automatically generates the PHP controller and view files in the component's `admin/views/` folder.

---

## Add Custom Button Sample

[00:04:12](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h04m12s)

You can add **custom toolbar buttons** within your Custom Admin View. These buttons trigger controller methods that perform specific actions.

1. In your Custom Admin View, scroll to the **Custom Buttons** section.
2. Click **Add**.
3. Configure:

   * **Icon** - Choose from Joomla's built-in icons.
   * **Name** - Example: `Edit Company`.
   * **Controller Method** - Example: `editcompany`.
   * **Target Type** - Select whether the button applies to a **single item**, a **list**, or **both**.
4. Click **Save**.

> **Note:** The button configuration is saved in the JCB form but not yet implemented in the database or PHP logic until the component is compiled.

[00:04:52](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h04m52s)

---

## Adding Scripts for Controller Methods

[00:05:05](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h05m05s)

Each button you create needs an associated **controller method** to define its behavior.

1. In the JCB backend, open your component and go to:
   **Custom Admin View → PHP Controller Script Area.**
2. Add your PHP logic for each custom button, for example:

```php
// Example controller method
public function gotocompanies()
{
    $this->setRedirect('index.php?option=com_costbenefitprojection&view=companies');
}
```

[00:05:16](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h05m16s)

You may also include related model logic by adding code in the **Model Script** section.
If no model script is needed, use comment placeholders (`//`) to suppress warnings.

[00:05:47](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h05m47s)

The `editcompany` method, for example, follows Joomla's convention for opening items securely, including CSRF token validation and permission checks.

[00:06:13](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h06m13s)

---

## Area for Custom Scripting

[00:06:17](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h06m17s)

JCB provides specific **code insertion areas** for Custom Admin Views, where you can safely add custom scripting.

If you're unsure where a particular code snippet executes:

1. Compile your component.
2. Search for the snippet text within the generated component files.
3. Observe its position in the PHP flow (controller, model, or view).

This makes debugging and customization straightforward.

---

## Combining Multiple Data Example

[00:06:58](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h06m58s)

In the **Combined Results** view, multiple company data entries can be selected and aggregated.
When you click **Combined Results**, JCB merges the selected records and renders a single structured output.

[00:07:16](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h07m16s)

The layout uses a combination of HTML and PHP, and can include templates for reusable design.

[00:07:41](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h07m41s)

> **Tip:**
> You can use **templates and layouts** interchangeably across **Site** and **Admin Views**.
> This ensures consistent design and code reuse throughout your component.

[00:08:11](https://www.youtube.com/watch?v=gtdQ1lwB9ds&t=00h08m11s)

---

## Summary

Custom Admin Views in JCB enable you to:

* Build **complex backend interfaces** with dynamic content.
* Integrate **custom scripts and controller logic**.
* Add **interactive toolbar buttons**.
* Reuse **layouts and templates** across multiple views.

They are powerful for displaying advanced data, combining results, or building specialized dashboards directly in your Joomla admin area.
