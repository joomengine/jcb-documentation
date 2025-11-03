# Adding Site Views to a Component in Joomla Component Builder (JCB)

Site Views in JCB define what users see on the front end of your Joomla component.

## Site View fundamentals

**Site Views** are the public-facing view of your Joomla component—JCB generates the Joomla-native model, view, and controller files for you while you decide how information appears. Each view combines:

- A **Main Dynamic Get** that determines how data loads (single record or lists).
- Any number of **Custom Dynamic Gets** to provide supplemental datasets.
- Integrated **Templates** and **Layouts** so you can organise markup and reuse presentation logic.
- Optional **Custom Code placeholders** where you can inject reusable frontend logic from snippets or repositories.
- Optional **JavaScript and CSS libraries** to enhance interaction or styling.

Because Site Views initiate the requests that Joomla plugins respond to, map each view to the plugin events it might raise. For example, views that render content typically fire `onContentPrepare`, while views that manage authentication hand-offs may involve `onUserLogin`. Coordinating Site View design with the [JCB! Joomla Plugins](./Joomla-Plugins.md) checklist keeps frontend interactions and background automation in sync.

Because every part is modular, you can reset a Site View to the maintained baseline whenever a repository updates, or fork it into your own repository when you need long-term customisation.

---

## [00:00:00](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h00m00s) - Accessing Component Settings

1. **Login to Joomla Administrator.**
   Open your Joomla backend and log in as an administrator.

2. **Navigate to Component Builder.**
   From the main menu, go to **Components → Component Builder → Components**.

3. **Select Your Component.**
   Open your existing component (for example, *Sermon Distributor*).

4. **Go to the Settings Tab.**
   Inside your component, locate the **Settings** tab.
   This is where both **Admin Views** and **Site Views** are managed.

---

## [00:00:25](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h00m25s) - Understanding Views

* **Admin Views:** Used to manage backend data and configuration.
* **Custom Admin Views:** Allow adding custom pages in the admin area.
* **Site Views:** Define the structure and data presented on the front end of your Joomla site.

To add or manage Site Views:

* Go to the **Custom Admin Views** and **Site Views** sections.
* Click **"Add Custom Admin View"** if you need new ones (Sermon Distributor, for example, has none).
* Move on to **Site Views** to configure your public-facing component views.

---

## [00:01:11](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h01m11s) - Fixing the Site Views Selection Glitch

You may notice that some Site View checkboxes or toggles appear **unselected** even though you selected and saved them earlier.

### Important

This is a **Joomla JavaScript glitch** - not an issue with JCB.

**How to handle it:**

1. If the Site View options look unselected after saving:

   * Close the Site View editor.
   * Reopen it again.
2. The selections should now appear correctly.
3. Avoid saving while the boxes are unchecked - this would save `null` values and cause unexpected results.

> **Tip:** The same issue can occasionally occur in Admin Views. Always double-check before saving.

---

## [00:02:21](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h02m21s) - Exploring Site View Options

Each Site View in JCB offers **four key switches**:

| Option           | Description                                                       | Typical Use                                                  |
| :--------------- | :---------------------------------------------------------------- | :----------------------------------------------------------- |
| **Menu**         | Adds this Site View as a selectable menu item in Joomla.          | Allows users to link the view from Joomla's menu system.     |
| **Metadata**     | Enables metadata (title, description, keywords) for this page.    | For SEO and browser metadata display.                        |
| **Default View** | Sets this view as the fallback (default) page for your component. | Used when no specific view is requested or access is denied. |
| **Access**       | Enables access control (permissions and groups).                  | Restricts who can view specific pages or data.               |

Let's break down each option below.

---

### [00:02:46](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h02m46s) - Menu Option

When **Menu = Yes**, JCB automatically creates an XML definition so Joomla recognizes the Site View as a menu type.

**Effect:**
After compiling the component:

1. Go to **Menus → Add New Menu Item** in Joomla.
2. Under **Select Menu Item Type**, your component's view (e.g., "List of Sermons") will now appear.
3. Selecting it will link the front-end display directly to that Site View.

> **Tip:** This saves time - you don't have to manually write XML for Joomla menu types.

---

### [00:03:47](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h03m47s) - Metadata Option

When **Metadata = Yes**, JCB adds metadata-handling scripts to your generated view.

**To make this work properly:**

1. Ensure your model passes metadata fields into the view.

   * Typically found in the `$this->item` or `$this->items` arrays.
2. Compile your component.
3. Open the generated file:
   `/components/com_yourcomponent/views/viewname/view.html.php`
4. Check that metadata is loaded and assigned properly.

If the data isn't present, Joomla won't display metadata even if the switch is enabled.

> **Tip:** Always verify that the model returns metadata for your Site View items.

---

### [00:04:53](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h04m53s) - Default View Option

The **Default View** acts as the component's **home page** or fallback route.

**Guidelines:**

* You can **only have one default view** per component.
* When Joomla can't determine which view to load, it automatically redirects to this one.
* It's also used as the fallback when a user lacks permission to access other views.

Example:
If your default view is **Preachers**, and a user visits a restricted "Sermon" view, they will be redirected back to "Preachers" with a message.

> **Important:** Do not select multiple default views. Only one should be active.

---

### [00:05:37](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h05m37s) - Access Option

The **Access** switch enables permission control for each Site View.

**Purpose:**
Allows JCB to include the necessary access tables so that:

* Users only see views they have permission for.
* Joomla's Access Levels (Public, Registered, Special, etc.) are respected.

**Implementation Details:**

* Access can be handled at both **item** and **view** levels.
* Uses **user groups** and **access levels** to control who can view what.
* When this option is checked, JCB ensures the access fields and logic are built into your component.

> **Tip:** Always configure access levels in Joomla after installation to match your component's logic.

---

## [00:06:32](https://www.youtube.com/watch?v=zZ_HJeYL8ps&t=00h06m32s) - Final Step: Compile and Test

Once you've configured your Site Views:

1. Click **Save & Close** in JCB.
2. Go to **Component Builder → Compile** and compile your component.
3. Install or update the generated component package in Joomla.
4. Open your Joomla front end and test:

   * The menu links.
   * Metadata presence.
   * Access restrictions.
   * Default view redirection.

> **Result:** Your Site Views are now active, accessible, and properly configured.

---

## Keep Site Views in sync across projects

Site Views ship from curated repositories. Whenever an upstream definition improves:

1. **Select** the Site Views you want to refresh in JCB.
2. Click **Reset** to pull in the latest maintained version.
3. Recompile your component so the generated MVC files include the updates.

If you need to diverge permanently, **fork the repository** that maintains the Site View, adjust it to your needs, and point JCB to your fork. This keeps your custom logic version-controlled while still benefiting from JCB's automatic generation.

---

## Summary

| Step | Action                                          | Notes                               |
| :--- | :---------------------------------------------- | :---------------------------------- |
| 1    | Open your component in JCB.                     | Go to *Settings → Site Views*.      |
| 2    | Fix unselected toggles if needed.               | Reopen before saving.               |
| 3    | Configure Menu, Metadata, Default View, Access. | Each adds key functionality.        |
| 4    | Compile your component.                         | Generates XML and PHP structure.    |
| 5    | Test in Joomla front end.                       | Confirm menu, access, and metadata. |

---

## Helpful Tips

* Always **reopen the Site View editor** before saving if selections appear off.
* Use **Menu = Yes** to expose the view to Joomla's menu manager.
* Only **one Default View** should ever be active.
* Use **Access Control** wisely to protect sensitive pages.
* After major changes, **recompile and reinstall** the component to apply updates.

---

**Video Reference:**
*Watch the full tutorial on YouTube:*
[Adding Site Views to a Component - Joomla Component Builder](https://www.youtube.com/watch?v=zZ_HJeYL8ps&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---
