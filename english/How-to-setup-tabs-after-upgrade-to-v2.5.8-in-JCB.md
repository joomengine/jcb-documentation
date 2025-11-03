# How to Set Up Tabs After Upgrade to JCB v2.5.8

This guide explains how to set up and manage **Tabs** in Joomla Component Builder (JCB) after upgrading to **version 2.5.8**.
It reflects the latest JCB interface and workflows, particularly within the **Admin Views** and **Admin Fields** sections.

---

## 1. Understanding the Tab System in JCB

[00:00:00](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

In JCB v2.5.8, the way **Tabs** are configured inside an **Admin View** has slightly changed.
Tabs help organize fields into logical sections within the backend of your Joomla component, making your admin interface cleaner and more user-friendly.

Tabs are now defined in the **Admin View's Settings** area and linked to fields through their **Tab selection dropdown**.

---

## 2. Adding Tabs in Admin View Settings

[00:00:00](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

### Steps to Add Tabs:

1. Open your **Admin View** in Joomla Component Builder.
2. Scroll down to the section labeled **Settings**.
3. Locate the area called **Tabs**.
4. Click the **Add (+)** button to create a new tab entry.
5. Name your tabs appropriately (e.g., `General`, `Options`, `Advanced`, `Permissions`).
6. After entering all desired tab names, **click "Save"**.

> **Tip:** Tabs are only stored in the database after saving.
> If you forget to save, your tabs will not appear in the dropdown list later.

When you save, JCB stores these tabs and makes them available as selectable options for your Admin Fields.

---

## 3. Assigning Fields to Tabs

[00:00:52](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m52s)

Once your tabs are created and saved, open the **Admin Fields** associated with that view.

1. Go to **Admin Fields** in JCB.
2. Edit or create a field.
3. In the **Tab** dropdown (found under the field settings), you will now see all the tab names you created earlier.
4. Select which tab each field should appear under.
5. Save the field.

When you later compile and install your component, the backend form will display the fields grouped under their respective tabs.

---

## 4. Behavior When No Tabs Are Defined

[00:01:29](https://www.youtube.com/watch?v=NFp_CtE0LZI&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m29s)

If no tabs are defined in the Admin View's **Settings**, JCB automatically defaults to showing all fields under a single tab called **Details**.

This means:

* The form will not show multiple tabs.
* All fields will appear in the "Details" section.

To have more than one tab, you must add them in the **Tab Setup Options** as described above.

---

## 5. Managing Tab Setup Options

If you later wish to rename or rearrange your tabs:

1. Reopen your **Admin View**.
2. Scroll to **Settings → Tabs**.
3. Edit the tab names or delete unneeded ones.
4. Click **Save** again to apply the changes.

> **Note:** Changing tab names will require you to update fields assigned to those tabs so they continue to match.

---

## 6. Compiling and Testing Your Component

After setting up your tabs and assigning fields:

1. Click **Compile** in JCB to build your component package.
2. Install the generated `.zip` file in your Joomla site.
3. Open the component's backend view to confirm your tabs appear as expected.

You should now see your fields grouped neatly under each tab, just as defined in your Admin View.

---

## 7. Summary

* Tabs are created inside **Admin View → Settings**.
* Fields link to tabs via their **Tab dropdown**.
* Always **Save** after creating or editing tabs.
* If no tabs exist, JCB defaults to the **Details** tab.
* Changes in tab setup must be followed by a recompile.

---

### Example Workflow Recap

| Step | Action                          | Result                 |
| ---- | ------------------------------- | ---------------------- |
| 1    | Add tabs in Admin View Settings | Tabs stored in DB      |
| 2    | Save Admin View                 | Tabs become selectable |
| 3    | Edit Admin Fields               | Assign fields to tabs  |
| 4    | Compile component               | Tabs appear in backend |

---
