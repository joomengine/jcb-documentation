# How to Add Joomla Custom Fields in Joomla Component Builder (JCB)

**Video Tutorial Reference:** [YouTube - How to Add Joomla Custom Fields](https://www.youtube.com/watch?v=n5RBmP0uNCM)
*(Timestamps throughout this guide correspond to the video above.)*

---

## Overview

[00:00:00](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h00m00s)

Joomla Custom Fields allow you to add additional data input options to Joomla entities such as **articles**, **users**, or **custom components**. Each custom field can be grouped into **Field Groups**, giving structured organization to data entry forms in Joomla.

With recent updates, **Joomla Component Builder (JCB)** now natively supports **Joomla Custom Field Integration**, enabling developers to include these fields directly in their generated components.

---

## 1. Understanding Joomla Custom Fields and Groups

Before diving into JCB integration, it's important to understand the Joomla custom field system:

* **Fields** are custom input options (e.g., text, list, image) attached to content.
* **Field Groups** organize fields into logical sets.
* In Joomla core, these are found under:

  * **Content → Fields**
  * **Content → Field Groups**

You can now create similar fields directly within your **JCB-generated component**, with full back-end and front-end functionality.

---

## 2. Linking Joomla Fields to an Admin View

[00:00:52](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h00m52s)

To make Joomla Custom Fields available within a JCB component:

1. **Open your component** in JCB.
2. Go to **Admin Views**.
3. Select or create an Admin View (e.g., `Look`).
4. Click **Edit** to open its settings.
5. Scroll to find the new **"Joomla Fields"** toggle.
6. Enable this option.

> **Note:** This adds Joomla Custom Field integration to the Admin View.
> Multiple Admin Views can support this integration if needed.

This ensures that custom fields will be available for data entry in the back-end form of that view.

---

## 3. Compile and Install the Component

[00:02:05](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h02m05s)

After enabling Joomla Fields:

1. **Compile** your component.
2. **Install** it on your Joomla site using the JCB compiler's installation process.

Once installed, navigate to your component in the Joomla back-end.
For example:

```
Components → Demo → Looks
```

You'll now see two new menu items:

* **Looks Fields**
* **Looks Field Groups**

---

## 4. Creating Fields and Field Groups

[00:02:34](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h02m34s)

1. Open **Looks Field Groups**.
2. Click **New** → Enter a **Title**, e.g., `Really Easy` → Save & Close.
3. Go to **Looks Fields** → Click **New**.
4. Choose a **Type** (e.g., `Text`).
5. Assign it to your `Really Easy` group.
6. Save & Close.

Now, when creating a new **Look** record, a **new tab** named `Really Easy` will appear with your custom field visible for input.

You can:

* Add multiple fields by assigning them to the same group.
* Add additional groups to organize fields.

> **Example:**
>
> * Field Group: `Really Easy`
> * Fields: `Simple Field`, `More Fields`

---

## 5. Adding Field Display Events to the Front-End

[00:04:42](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h04m42s)

By default, fields work out-of-the-box in the **back-end**, but to display them in the **front-end**, you must use **Joomla content plugin events**.

JCB provides these through the **Dynamic Get Builder**.

### Steps:

1. In JCB, go to **Dynamic GETs**.
2. Select the **Get Item** for your front-end view (e.g., `Looking`).
3. Under **Content Plugin Events**, select:

   * `onContentAfterTitle`
   * `onContentBeforeDisplay`
   * `onContentAfterDisplay`
4. Save and close.

These events control when and how Joomla fields are displayed.

---

## 6. Compiling to Inject Event Code

[00:07:30](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h07m30s)

After enabling the events:

1. **Recompile** the component in JCB.
2. **Inspect** the generated code:

   ```
   components/com_demo/views/looking/view.html.php
   ```
3. The display function now includes:

   * Event dispatcher loading
   * Content plugin triggers:

     * `onContentAfterTitle`
     * `onContentBeforeDisplay`
     * `onContentAfterDisplay`

These calls notify Joomla to retrieve and render any assigned custom fields.

---

## 7. Adjusting the Context

[00:09:51](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h09m51s)

If your Admin View name differs from your Site View (e.g., `Look` vs `Looking`), you need to adjust the **Context**.

1. Go to **Site Views**.
2. Open your **front-end view** (e.g., `Looking`).
3. Locate the new **Context** field.
4. Set the Context to match the Admin View (`Look`).
5. Save & Close.
6. Recompile.

This ensures field data linked to `com_demo.look` displays correctly in the front-end.

> **Tip:**
> Joomla fields rely on matching context identifiers.
> Misalignment (e.g., `look` vs `looking`) will prevent field data from displaying.

---

## 8. Displaying Fields in Your Template

[00:16:42](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h16m42s)

To output field values in your template:

1. Open your component's **Site View template file**:

   ```
   components/com_demo/views/looking/tmpl/default.php
   ```
2. Use event placeholders where appropriate:

   ```php
   <?php echo $this->item->event->afterDisplayTitle; ?>
   <?php echo $this->item->event->beforeDisplayContent; ?>
   <?php echo $this->item->event->afterDisplayContent; ?>
   ```
3. Adjust placement based on where you want fields to appear (before title, after content, etc.).
4. Save, recompile, and test on the front-end.

---

## 9. Testing and Troubleshooting

[00:20:08](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h20m08s)

* If fields don't display:

  * Confirm the **Context** matches.
  * Ensure the correct **event variables** are used.
  * Check that **Dynamic GET events** are selected and compiled.
* You can reposition field output by editing their **Automatic Display** setting:

  * Before Display
  * After Title
  * After Display
  * Do Not Automatically Display

> **Example Adjustment:**
>
> * Move "Simple Field" to display after content:
>
>   * Open the field in Joomla → set "Automatic Display" to "After Display".

---

## 10. Optional: Hide Field Labels

[00:22:20](https://www.youtube.com/watch?v=n5RBmP0uNCM&t=00h22m20s)

To hide a field label in the front-end display:

1. Edit the field in Joomla.
2. Set **"Show Label" → "Hide"**.
3. Save and refresh.

Only the field value will appear on the page.

---

## 11. Final Notes

This integration provides seamless support for Joomla Custom Fields in JCB-generated components.
You can now:

* Create and manage **Field Groups** and **Fields**.
* Use **Dynamic GET Events** to trigger field rendering.
* Control field placement and visibility.
* Extend functionality through **content plugins** and **custom code**.

> **Tip:** This setup mimics Joomla's native article field behavior, ensuring that your JCB components integrate naturally within the Joomla ecosystem.

---

### Summary Workflow

| Step | Action                             | Area             |
| ---- | ---------------------------------- | ---------------- |
| 1    | Enable Joomla Fields in Admin View | JCB Admin View   |
| 2    | Compile and Install                | JCB Compiler     |
| 3    | Create Field Groups and Fields     | Joomla Backend   |
| 4    | Enable Content Plugin Events       | JCB Dynamic GET  |
| 5    | Adjust Context                     | JCB Site View    |
| 6    | Recompile Component                | JCB Compiler     |
| 7    | Edit Template to Display Fields    | Site Template    |
| 8    | Test and Adjust Display            | Joomla Front-End |
