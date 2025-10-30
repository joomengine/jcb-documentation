# Quick Subform Demonstration

**Tutorial Source:** [YouTube – Quick Subform Demonstration](https://www.youtube.com/watch?v=3j4xPQC4apI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
**Author:** Joomla Component Builder Team
**Purpose:** Learn how to create and implement subforms in Joomla Component Builder (JCB).
**Difficulty Level:** Beginner to Intermediate

---

## 1. Introduction – Community Request

**[00:00:00](https://www.youtube.com/watch?v=3j4xPQC4apI&t=0s)**

A community member asked for guidance on how to generate and handle subforms in Joomla Component Builder (JCB), specifically:

* How to generate a subform directly within JCB.
* Where to find the XML details for repeated subform fields.
* How subform data is populated, validated, and saved.

They assumed this functionality was automated within JCB, without needing manual XML editing.
While earlier tutorials covered *repeatable fields*, those have since been **discontinued** and replaced by the more powerful **subform field type**.

---

## 2. Understanding Subforms

**[00:01:13](https://www.youtube.com/watch?v=3j4xPQC4apI&t=73s)**

A **subform** in Joomla allows you to group several fields together into a single fieldset that can be repeated.
Each instance of a subform acts as a mini form inside your main form — ideal for storing related sets of data.

**Example use case:**

* A "Team Members" section where each member has *Name*, *Email*, and *Website* fields.

### In JCB

JCB simplifies this by:

* Automatically generating the correct XML for the subform.
* Handling JSON storage automatically.
* Managing both the loading and saving of subform data through its compiler.

---

## 3. Step 1 – Create the Fields for Your Subform

**[00:01:44](https://www.youtube.com/watch?v=3j4xPQC4apI&t=104s)**

Each subform requires a set of standard fields (for example: *Name*, *Email*, *Website*, *Description*).
Before creating the subform field itself, these individual fields must exist in JCB.

### To Create the Fields

1. In JCB, go to **Admin → Fields**.
2. Click **New**.
3. Choose the appropriate **field type** (e.g., *Text*, *Email*, *Checkbox*, *List*).
4. Configure each field as desired.
5. Save each one individually.

**Tip:** Use clear field names and labels — they will appear inside the subform.

---

## 4. Step 2 – Create the Subform Field

**[00:02:06](https://www.youtube.com/watch?v=3j4xPQC4apI&t=126s)**

Once your base fields exist, you can create the subform that will reference them.

### Procedure

1. Go to **Admin → Fields** and click **New**.
2. Set **Field Type** to `Subform`.
3. JCB will automatically populate a basic XML structure for the subform.
4. Give the field a **label** and **name** (for example: `Options` or `options_test`).
5. Assign a **data type** – usually `TEXT` or `MEDIUMTEXT`.

   * JCB automatically detects that this field is a subform and handles JSON encoding/decoding when storing or loading data.
6. Save the new field.

---

## 5. Step 3 – Assign the Fields to the Subform

**[00:04:57](https://www.youtube.com/watch?v=3j4xPQC4apI&t=297s)**

Each subform must reference existing field IDs to know which fields to include.

### How to Add Fields by ID

1. Find the **IDs** of the fields you previously created.

   * Go to **Admin → Fields** and note the numerical IDs in the list view.
2. In your subform field configuration, locate the **"Fields"** input area.
3. Enter a comma-separated list of field IDs (e.g., `199,280,100`).

   * Example:

     ```
     Fields: 199,280,100
     ```

   This will include *Name*, *Website*, and *Email* in your subform.

---

## 6. Step 4 – Configure Additional Options

**[00:05:33](https://www.youtube.com/watch?v=3j4xPQC4apI&t=333s)**

JCB allows you to customize the behavior and validation of your subform fields.

| Option          | Description                                                                 |
| --------------- | --------------------------------------------------------------------------- |
| **Description** | Optional text describing what this subform does.                            |
| **Maximum**     | The maximum number of repeatable entries allowed.                           |
| **Filter**      | Defines how each field value is validated (e.g., `string`, `email`, `url`). |
| **Showon**      | Controls conditional display of the subform based on another field's value. |

**Validation Notes:**
Each field in a subform is validated according to its own field type and filter.
You do not need to add custom validation unless you want advanced logic.
JCB automatically integrates Joomla's native field validation when compiling.

---

## 7. Step 5 – Optional: Form Source File

**[00:03:51](https://www.youtube.com/watch?v=3j4xPQC4apI&t=231s)**

The **Formsource** option allows you to load an external XML file defining the subform layout.
However, this is **optional** in JCB since it already generates XML automatically.

* Use **Formsource** only if you maintain custom XML outside JCB (for example, an XML file in your component's `models/forms` folder).
* You can use **either** the `Fields` option **or** `Formsource` — not both.

If you include a `Formsource`, JCB's compiler recognizes it and handles it correctly during component compilation.

---

## 8. Step 6 – Add the Subform to a View

**[00:08:19](https://www.youtube.com/watch?v=3j4xPQC4apI&t=499s)**

Once your subform field is created, add it to any **Admin View** in your component.

### Example

To add the subform `Options (test)` to the **Look** view:

1. Open your **Admin Views** in JCB.
2. Select the **Look** view (from the *Demo* component).
3. In the *Fields* tab, add the subform field `Options (test)` under the **Details** section.
4. Set the display width (for example, full width).
5. Save the view.

---

## 9. Step 7 – Compile and Install the Component

**[00:08:49](https://www.youtube.com/watch?v=3j4xPQC4apI&t=529s)**

Now that your subform is part of a view:

1. Go to **Components → Joomla Component Builder → Compile**.
2. Compile the component that contains your subform.
3. Install or update it in Joomla via the **Extensions Installer**.

---

## 10. Step 8 – Test the Subform in Joomla

**[00:09:26](https://www.youtube.com/watch?v=3j4xPQC4apI&t=566s)**

Navigate to your component in the Joomla backend:

1. Open the view that contains your subform (e.g., *Looks* in the Demo component).
2. Add data in the subform fields (e.g., Name, Website, Email).
3. Click the **"+" (Add)** button to add another set of fields.
4. Enter multiple entries and save.

**Result:**
The subform data is stored as JSON in the database, and when you reopen the record, the values are loaded and displayed correctly.

**[00:10:45](https://www.youtube.com/watch?v=3j4xPQC4apI&t=645s)**
You can reorder entries (drag and drop or using the ordering arrows), save again, and the order will persist.

---

## 11. Summary

Subforms in Joomla Component Builder allow for powerful, flexible data structures inside your components without writing manual XML or PHP.

### Key Points:

* Create all individual fields first.
* Use the Subform field type to group them.
* Assign fields by their IDs.
* Set data type to `TEXT` or `MEDIUMTEXT`.
* Add the subform to your desired view.
* JCB automatically handles saving and loading logic.

---

## 12. Additional Resources

* **Joomla Component Builder Tutorials (YouTube):**
  [https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE](https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

* **Official JCB Documentation:**
  [https://git.vdm.dev/joomla/pkg-component-builder/wiki](https://git.vdm.dev/joomla/pkg-component-builder/wiki)

---

### Helpful Tips

* Always test subforms on a small scale before implementing complex logic.
* Avoid nesting subforms (they can cause complex data structures).
* Use **Custom Code Areas** in JCB if you need to manipulate subform data programmatically.
