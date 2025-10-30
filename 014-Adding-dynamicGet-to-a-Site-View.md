# ADDING DYNAMICGET TO A SITE VIEW

(*Based on JCB Tutorial Video and Transcript*)

---

### Checking The Target Dataset

[00:00:00](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m57s)

Now that the DynamicGet is in place, the next step is to **add it to a Site View** and observe how it functions within the component.

1. Navigate to **Site Views** in Joomla Component Builder.
2. Click **New** to create a new Site View.
3. For this example, since a Site View already exists, open the **Preacher** view.

This setup will allow you to connect the previously created DynamicGet methods to your Site View.

---

### Populate Fields From Get's

[00:00:32](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m32s)

On the right-hand side of the Site View editor, you'll find **three key fields** for populating DynamicGet methods:

1. **Custom DynamicGets** -

   * Add one or more custom DynamicGet methods here.
   * These are additional queries or data sets you might want to use in the same view.

2. **Main DynamicGet** -

   * This is the **primary** DynamicGet method.
   * Only one main DynamicGet can be added per Site View.
   * It determines how the model retrieves data (via either `getItem` or `getItems`).

3. **Custom DynamicGets (optional)** -

   * You can include as many custom DynamicGets as needed.
   * These will provide additional data objects to the view.

> **Tip:** The main DynamicGet determines whether the data retrieved is a list (`getItems`) or a single item (`getItem`).

---

### Dynamic Values

[00:01:36](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m36s)

The **third field** in the Site View editor is for **Dynamic Values**.
These are snippets of code automatically generated to help you implement DynamicGet data in your view.

You can select:

* **Main Gets** - display data from the main DynamicGet.
* **Custom Gets** - display data from your custom DynamicGets.
* **Both** - show all DynamicGet options together.

[00:02:04](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m04s)

When you select a main get, it shows a **printout of code examples** demonstrating how to access the result set in your views.

[00:02:32](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m32s)

Each code block can be copied easily:

* **Right-click and copy** or use **Ctrl+C / Cmd+C**.
* You can also select only a portion of the code (e.g., without the `echo` statement).

[00:03:05](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m05s)

> **Note for macOS users:** Once you release the mouse, macOS may auto-select the full block. To copy a part, press **Cmd+C** before releasing.

---

### Inserting Values Into View

[00:03:36](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m36s)

Use the **Dynamic Values** code within your view's PHP template to display the retrieved data.
For instance, in the Preacher view:

* Ensure you have a valid Preacher object.
* Use the provided code snippet to **check whether the main data items are loaded** on the page.
* Typical main items include `sermons`, `preacher.id`, or the `getList` dataset.

[00:04:08](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s)

These items are stored in arrays (`items`) that can be looped through to display data dynamically.

[00:04:38](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m38s)

Templates are then used to handle different **display layouts** for this data.

---

### Making Use of Data Being Passed Through to the View

[00:05:19](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m19s)

Each Custom Get provides a data structure that defines how its results are packed and passed into the view.

[00:05:36](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m36s)

For example:

* A method named `numbersermons` would make its data available as `$this->numbersermons`.
* This structure may vary depending on how you modify your component's custom code.

> **Tip:** Use Dynamic Values to preview how the data would look before making custom modifications.

---

### Var Dump

[00:06:13](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m13s)

To understand the structure of your dataset:

1. Insert a `var_dump()` at the desired data point in your template.
2. Rebuild the component.
3. View the output on the frontend to inspect the data structure.

[00:06:45](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m45s)

This helps identify whether the data is an array, object, or nested structure, allowing you to adjust your access logic accordingly.

[00:07:20](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m20s)

Repeat this step for other Custom Gets if needed to verify their data structures.

---

### Gets In The Code (e.g., Preacher.php)

[00:07:33](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m33s)

To see how Custom Gets become available in your Site View, open the **model file** - for example, `preacher.php`.

[00:07:55](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m55s)

Inside the model, locate the `getListQuery()` method.
Here you'll see how the main and joined tables are defined:

* `sermon` as `a`
* `series` as `c`
* `preacher` as `d`
* `categories` as `b`

[00:08:18](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m18s)

These joins determine how data is retrieved, filtered, and returned to the view.

[00:08:41](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m41s)

Back in the JCB interface, you'll notice that the main DynamicGet (e.g., `sermon (preacher.id) getlist`) matches the structure used in this model.

---

### Looking At The Dynamic Get

[00:09:06](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m06s)

When viewing the DynamicGet definition inside JCB:

* `Sermon` is set as the main table (`a`).
* `Series` (`c`) and `Preacher` (`d`) are joined for selection values.
* `Statistics` (`e`) is a **list** join, meaning multiple entries.
* `Category` (`b`) is added as a **single** join.

[00:10:01](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m01s)

In the code, this configuration appears in `getItem()` and its supporting methods, ensuring that statistics and related data are available for each item.

[00:10:30](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m30s)

Custom methods defined in DynamicGet can also be added to return additional values for use in the Site View.

---

### Preacher view.html.php Generated Code

[00:10:55](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h10m55s)

In the generated **view.html.php** file for the Preacher view:

* The method `getItems()` retrieves the dataset from the model.
* These items are then stored as `$this->items` within the view class, making them available for use in your templates.

[00:11:26](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m26s)

Selecting the corresponding DynamicGet in JCB shows that the variables match the generated code fields (like `id`, `asset_id`, etc.).

---

### Checking The Target Datasets

[00:11:48](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h11m48s)

Inspecting deeper in the code, you'll notice keys such as `idsermonstatisticsE`, which represent array values containing further subarrays.

[00:12:03](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m03s)

You can target these datasets by referencing their corresponding keys.

[00:12:28](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m28s)

Each **Custom Get** (such as `preacher` or `numberdownloads`) contributes its own data structure that is accessible from the view.

[00:12:53](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m53s)

In the `view.html.php` file, these values are linked to variables like `$this->preachernumberdownloads` or `$this->numbersermons`.

---

### Site Preacher Tmpl Folder

[00:13:33](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m33s)

All Site View templates are stored under:
`/components/com_yourcomponent/views/preacher/tmpl/`

[00:13:50](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m50s)

The **default.php** file represents the main output layout, while other layout templates (in the `layouts` folder) can extend or override this default layout.

[00:14:24](https://www.youtube.com/watch?v=vEJZe6XqHJE&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m24s)

---

## Summary

By linking a **DynamicGet** to a **Site View**:

* You enable JCB to automatically load complex joined data structures into your frontend view.
* Use **Dynamic Values** to preview and insert code snippets for accessing this data.
* Inspect datasets using `var_dump()` to understand their structure.
* Display results dynamically through your view templates and layouts.

> **Next Step:** Experiment by creating your own Custom Gets, attach them to different Site Views, and review the generated model code to understand how JCB automates this data flow.
