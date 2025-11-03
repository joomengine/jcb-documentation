# DynamicGet

*(Using Sermon Distributor - Preacher Get Example)*

[00:00:00](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
*Click on the timestamp links to view the relevant section in the video.*

---

## Overview

In this tutorial, we explore how to create and configure a **Dynamic Get** in **Joomla Component Builder (JCB)**. The **Dynamic Get** allows you to dynamically fetch data from your component's backend views or even other installed components.

Using the *Sermon Distributor* component as an example, this guide demonstrates how to create a `preacher` get method, configure joins, filters, and pagination, and see how it translates into PHP code during compilation.

---

## Step 1: Selecting the Data Source

[00:00:25](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m25s)

1. Go to **Dynamic Get Builder** in JCB.
2. Begin with a new or existing Dynamic Get.
3. Select your **Source** type. Usually, you'll start with **"Back-end view"**, as it provides the most direct integration with your component's data.

> **Tip:** Selecting "Back-end view" ensures stability since the "Joomla Database" option may not yet be fully reliable for all components.

---

## Step 2: Understanding the Source Options

[00:00:50](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m50s)

There are three main data source options:

1. **Back-end View** - Recommended. Pulls data directly from one of your component's views.
2. **Joomla Database** - Enables fetching data from *any* component's database tables.

   * Use with caution: complex table structures or relationships can cause issues.
3. **Custom Get** - Lets you add your own PHP logic manually or let JCB generate it for you.

[00:02:55](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m55s)

When using **Custom Get**, you can either:

* Write the PHP code yourself, or
* Use "Custom - dropdown" to have JCB generate the structure for you automatically.

---

## Step 3: Loading the View Fields

[00:03:20](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m20s)

1. After selecting the **Back-end view** (for example, *Preacher*),
   JCB automatically loads all the field names of that view.
2. Each row represents a field that will be retrieved when the Get is executed.
3. The variable name column defines how the data will appear in the model.

> **Note:** Avoid changing system fields like `asset_id`. You can remove unneeded rows, but leave key identifiers intact.

---

## Step 4: Get Types and Their Purpose

[00:04:23](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m23s)

JCB provides four **Get Types**:

| Get Type       | Description                       | Typical Use         |
| -------------- | --------------------------------- | ------------------- |
| `getitem`      | Retrieves a single record         | Detail view         |
| `getlistquery` | Retrieves multiple records        | List or table view  |
| `getcustom`    | Custom secondary query (single)   | Supplementary data  |
| `getcustoms`   | Custom secondary query (multiple) | Additional datasets |

Only **one** `getitem` or `getlistquery` can exist per view.
You may, however, add multiple `getcustom` or `getcustoms` methods.

> **Tip:**
> Think of `getitem` / `getlistquery` as your **main methods**, while the `getcustom` ones are **secondary**, used to fetch supporting data.

---

## Step 5: Pagination in List Queries

[00:06:29](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m29s)

When using `getlistquery`, you can enable or disable pagination.

* **Yes** → Limits the results based on Joomla's **Global List Limit** (set under *System → Global Configuration → Default List Limit*).
* **No** → Returns all results (useful for AJAX calls).

If pagination is enabled, JCB automatically generates pagination code for both the **model** and **view**, producing standard page navigation such as `1, 2, 3`.

> **Note:**
> If Bootstrap or UIkit is not active on your template, the pagination styling may need adjustment.

---

## Step 6: Joining Other Tables or Views

### 6.1 - Join Data Views

[00:08:47](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m47s)

You can join your main data source with:

* **Categories (cb_categories)**
* **Other component views**

For instance, adding a *category field* automatically integrates Joomla's category system into your component.

### 6.2 - Joint View Tables

[00:10:23](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m23s)

You can:

* Join single or multiple rows from other views
* Rename field prefixes (e.g., `series_name`) to avoid conflicts
* Use **AS** aliases (limited from `a` to `zz`) to map joined tables uniquely

The *Return Row Type* can be:

* **Single** → One record joined
* **Multiple** → Multiple related records joined

Define the relationship using the **On Field** mapping (e.g., `a.series = c.id`).

---

## Step 7: Reviewing the Generated Code

[00:14:52](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m52s)

After compiling the component:

* The generated model method will include your Get logic.
* You can find it inside the **frontend model** (since Gets are typically used there).

Observe how JCB writes:

* The main query
* Joins (`series`, `preacher`, `statistics`)
* Aliases and return objects

It uses Joomla's **Database API** to safely quote and join values, creating an array of selected fields and their aliases.

---

## Step 8: Custom Script Area

[00:21:48](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m48s)

Within **Dynamic Get**, JCB offers a *Custom Script* area where you can insert PHP code that executes:

* **Before getting items**, or
* **After getting items**

This enables you to manipulate or validate the data once the Get query has run.

> **Example Use Case:**
> Modify or extend the dataset after fetching the items, or filter results dynamically before retrieval.

---

## Step 9: Filters, Where Clauses, and Global Settings

[00:24:04](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h24m04s)

The **Filter** and **Where** configuration defines how your data is restricted.

### Filter Types

Supported filters include:

* Categories
* User, Group, or Access Level
* Variable or Array
* Value and Repeatable Value

Some (like *Date*) are not yet fully implemented.

### Global Variables

Set **Global** or **State** variables to reuse Get values in other model areas.
Globals are most effective with `getitem`, since the return is a single record.

> **Example:**
> Use `JRequest::getInt('id')` as a filter to load data based on the URL parameter.

---

## Step 10: Default Access and Authorization

[00:27:38](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m38s)

JCB automatically injects access control logic into every Get model:

* User ID
* Group
* Authorized View Levels
* Application and Input values

You can use these global variables in your PHP code without manually retrieving them.

---

## Step 11: "Where" and "Ordering" Logic

[00:29:48](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m48s)

### Where:

Add conditional logic, such as:

```
a.state = 1
```

This ensures only published items are returned.

### Ordering:

[00:30:32](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m32s)

Define the ordering of items in the query:

* Field: `a.ordering`
* Direction: Ascending / Descending

You can add multiple order statements as needed.

---

## Step 12: Dynamic Get in Use (Preacher Example)

[00:31:45](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h31m45s)

In this example:

* The `getpreacher` function (a `getcustom`) retrieves a single preacher.
* It includes filters for publication state and access levels.
* It integrates with **UIkit**, dynamically loading required CSS/JS components when the view renders.

[00:36:00](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h36m00s)

Component Builder automatically adds the necessary helper methods to identify and load these UIkit components dynamically based on your content.

---

## Step 13: Applying Dynamic Get in Views

[00:39:12](https://www.youtube.com/watch?v=OPuCoxPW35s&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h39m12s)

Once configured, your **Dynamic Get** can be assigned to:

* **Site Views**, or
* **Custom Admin Views**

They are responsible for fetching the data that populates your views.
Essentially, the Dynamic Get defines **what** data to pull and **how** it is structured before being rendered in your component.

---

## Summary

| Feature               | Description                                  |
| --------------------- | -------------------------------------------- |
| **Main Types**        | `getitem`, `getlistquery`                    |
| **Custom Extensions** | `getcustom`, `getcustoms`                    |
| **Pagination**        | Optional automatic inclusion                 |
| **Join Tables**       | Supports single/multiple joins with aliasing |
| **Filters/Where**     | Build advanced query logic                   |
| **Global Access**     | Automatic injection of Joomla ACL context    |
| **Custom Script**     | Add pre/post-query PHP code                  |

---

### Key Takeaways

* Always start with **Back-end view** for stability.
* Use **pagination** when dealing with large datasets.
* Properly set **joins** and **aliases** to avoid conflicts.
* Leverage **custom scripting** for advanced data manipulation.
* JCB automates much of the model code - focus on configuring logic rather than writing it manually.

---
