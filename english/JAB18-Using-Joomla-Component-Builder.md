# JAB18 Using Joomla Component Builder (JCB)

Joomla Component Builder (JCB) is a powerful open-source tool for building Joomla components directly within your Joomla environment. It offers a complete, model-driven development workflow that allows developers to generate robust components without repetitive manual coding.

[00:00:00](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

---

## 1. Why Use a Component-Building Tool?

[00:00:40](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m40s)

Component creation in Joomla traditionally involves repetitive work-manually writing boilerplate code, setting up MVC folders, and maintaining naming conventions. Tools like Component Creator and JoomDD exist to automate parts of this process, but JCB goes further by offering:

* **Complete local control:** JCB runs directly in your Joomla installation.
* **No SaaS dependency:** Everything happens within your environment.
* **Open-source access:** The compiled source is open; you can inspect, modify, and redistribute.
* **Round-trip capability:** You can modify your generated component and re-import changes back into JCB.

Unlike SaaS tools that limit you to a few tables or features, JCB has no such restrictions.

---

## 2. Understanding the JCB Environment

[00:02:18](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m18s)

JCB is a **component that builds other components**. Once installed, you work entirely from within Joomla's administrator interface. The component builder itself was built using JCB - a testament to its power and self-sustainability.

### Key Features

* Full MVC component generation
* Built-in support for ACL, multilingual, versioning, and custom fields
* Integration of libraries, templates, and layouts
* Round-trip compilation and synchronization of code edits

---

## 3. Starting with the Dashboard

[00:12:35](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m35s)

After installation, JCB's **Dashboard** serves as your control center. From here, you can access:

* **Wiki and Tutorials:** All JCB guides and video tutorials.
* **Component Management:** Add, edit, or manage components.
* **Global Configuration:** Access to system-wide options and library settings.

The dashboard also includes a **Wiki link** that points to JCB's official documentation and video index, making it easy to explore tutorials on topics like field creation, views, and dynamic data handling.

---

## 4. Builder Workflow Overview

[00:14:16](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m16s)

The JCB workflow follows a logical structure:

1. **Create a Component**
2. **Define Field Types**
3. **Create Fields**
4. **Build Views (List, Item, or Custom)**
5. **Link Data with Dynamic GET**
6. **Add Templates, Layouts, and Libraries**
7. **Integrate Custom/Bespoke Code**
8. **Compile and Install**
9. **Collaborate or Export Packages**

This flow ensures your component is cleanly generated and fully functional with Joomla's native architecture.

---

## 5. Creating a Component

[00:15:04](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m04s)

Go to **Components → Joomla Component Builder → Components → New**.

### Tabs Overview

* **Details:** Define component name, prefix, and debugging settings.
* **Settings:** Configure component behaviors and options.
* **Admin & Site Views:** Manage the administrator and frontend interfaces.
* **Libraries & Helpers:** Include reusable PHP helpers or external libraries.
* **Dashboard:** Customize the admin dashboard for your component.
* **MySQL Data:** Define initial SQL data or table creation scripts.
* **ReadMe:** Add documentation that will ship with your component.

---

## 6. Defining Field Types and Fields

[00:16:26](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h16m26s)

### Field Types

Field Types define reusable input structures - e.g., text, calendar, category, checkbox, color, or custom inputs. They are **global** across all your components, promoting reusability.

### Fields

[00:17:28](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h17m28s)

Each field represents a database column and instance of a field type. You can:

* Assign labels, tooltips, and default values
* Configure field validation rules
* Attach filters and search behavior
* Define visibility per view (Admin/Site)

> **Tip:** Use field attributes to control sorting, filtering, and permissions at a granular level.

---

## 7. Creating Views

[00:18:59](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m59s)

Views define how your data is presented.

### Types of Views

* **List View:** Displays a table of items with filters and batch tools.
* **Item View:** Displays detailed information about a single record.
* **Custom View:** Enables specialized layouts such as reports or dashboards.

You can assign fields to each view, configure permissions, and define custom behaviors like:

* Ajax calls for item retrieval
* Post-save triggers
* Custom query filters

### Linked Fields

[00:22:17](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m17s)

Views show the linked fields and their configuration (sortable, searchable, required). You can also set visibility per tab or conditionally show fields.

### Conditional Logic

[00:23:05](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m05s)

Define field conditions to control when a field is displayed based on other field values-ideal for cleaner, context-sensitive forms.

---

## 8. Layouts, Templates, and Libraries

[00:23:55](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h23m55s)

### Templates

Manage PHP view files (e.g., `default.php`) and break them into smaller, reusable **sub-layouts**.

### Layouts

[00:24:37](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m37s)

Layouts define the structure of frontend and backend elements, fully compatible with Joomla's layout system.

### Libraries

[00:25:04](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h25m04s)

You can integrate external CSS/JS libraries (e.g., Bootstrap, UIKit) using a CDN or local path. Each reference is automatically loaded where required.

---

## 9. Using the Dynamic GET Builder

[00:26:52](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m52s)

The **Dynamic GET** feature lets you build advanced database queries visually.

* **Filters:** Restrict data by access level, publication state, or user-defined conditions.
* **Sorting:** Define default orderings and override them dynamically.
* **Global Variables:** Create and reuse dynamic global parameters.

### Table Joins

[00:29:16](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m16s)

Use joins to combine multiple tables into one dataset. You can add as many joins as needed-inner, left, or right-directly through the GUI. This provides a relational model without writing SQL manually.

---

## 10. Adding Custom and Bespoke Code

### Custom Code

[00:31:16](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h31m16s)

You can define reusable code snippets that JCB automatically injects at compile time. These snippets centralize logic across your component.

### Bespoke Modifications

[00:32:17](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h32m17s)

Bespoke code is JCB's most powerful feature-it allows you to insert or modify code anywhere within the compiled component.

When you rebuild, JCB:

* Extracts and reinserts your modifications
* Updates only the changed portions
* Keeps your logic intact during upgrades or Joomla version changes

This ensures **true round-trip development**-you can edit generated code safely and rebuild anytime without losing your changes.

---

## 11. Compiling Your Component

[00:35:57](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h35m57s)

Once your component structure is ready:

1. Open **JCB → Compile**.
2. Select your component from the list.
3. Click **Compile Component**.

After compiling:

* You can **install it immediately** on your site.
* Or **download the ZIP package** for external use.
* JCB automatically creates all MVC folders and MySQL tables.

You can also **export/import** packages to move projects between Joomla installations.

---

## 12. Collaborative Development

[00:38:48](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h38m48s)

JCB supports **Git-based collaboration**:

* Each component can be version-controlled in Git.
* Multiple developers can work independently and merge changes.
* The "mapped component" (the JCB project file) can be shared and forked.

> **Tip:** This approach prevents Joomla's record-locking issue, allowing parallel development.

---

## 13. Package Distribution and Giveaways

[00:40:29](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h40m29s)

VDM, the creator of JCB, now provides **free access** to key example packages:

* Joomla Component Builder
* Question and Answer Component
* Sermon Distributor

Users can obtain keys by forking or starring the public repositories and then importing them via JCB's **Import Packages** feature.

---

## 14. Final Notes and Community Contribution

[00:44:29](https://www.youtube.com/watch?v=S9heClCWJrg&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h44m29s)

JCB's open-source model encourages collaboration. By contributing improvements or sharing your components, you help grow a powerful ecosystem for Joomla developers.

> "The fact that you can modify any location within your component and still maintain round-trip development is what makes JCB unique."

---

### Summary

| Feature                  | Description                                   |
| ------------------------ | --------------------------------------------- |
| **Local Development**    | Build components directly within Joomla       |
| **Reusable Field Types** | Create once, use across multiple projects     |
| **Dynamic GET**          | Visually define database joins and filters    |
| **Bespoke Code**         | Safely insert and persist custom logic        |
| **Compiler**             | Generates complete installable ZIP packages   |
| **Collaboration**        | Git integration for shared component building |

---
