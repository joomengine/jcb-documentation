# **Adding Custom Admin Views to a Component**

---

## **Overview**

In Joomla Component Builder (JCB), *Custom Admin Views* allow developers to create dynamic and flexible administrative views inside their components. These views enhance the backend interface by providing additional dashboard sections, menu links, and functionality such as custom buttons and result displays.

In this example, we'll use the **Cost-Benefit Projection** component to demonstrate how to add and configure *Custom Admin Views* in JCB.

---

## **1. Accessing the Custom Admin Views Section**

1. Open **Component Builder** in your Joomla administrator panel.
2. Navigate to **Settings → Custom Admin Views**.
3. Click **New** to create a new Custom Admin View.

You'll notice that a *Custom Admin View* has more configuration options than a *Site View*. This is because the admin side is designed to be more dynamic and integrated into Joomla's administrative interface.

---

## **2. Understanding the Custom Admin View Options**

### **Icons and Menu Placement**

Each Custom Admin View can be associated with a **menu icon** and can appear in one or more of the following locations:

* **Main Menu** - The primary menu visible on the Joomla component dashboard.
* **Dashboard (List of Records)** - The central area displaying key data or quick links.
* **Submenu** - The vertical sidebar visible when navigating inside component views.

These settings control how your view will appear and how users will access it from the backend.

> **Tip:**
> Use distinctive icons for each Custom Admin View to make navigation intuitive. JCB supports Joomla's standard icon classes.

---

## **3. Targeting Specific Items and Views**

Custom Admin Views can target other views or items inside your component. This allows you to create contextual buttons or data summaries that directly link to related items.

1. In your new Custom Admin View, find the **Target View** dropdown.
2. Select the appropriate target (for example, `Company`).
3. Set **Has Metadata** and **Add Access** to `Yes` if needed.

This ensures that the Custom Admin View interacts correctly with the targeted view and has proper access permissions.

> **Example:**
> If your `Company Results` view should display data related to specific companies, set the target view to `Company`.

---

## **4. Linking the Custom Admin View Inside the Component**

After configuration, open your component's **Dashboard** or **Target View** (for example, *Companies*) and check the new button or icon that appears.

When correctly configured:

* The **Company Results** button will appear in the toolbar or dashboard.
* Clicking it will open the *Custom Admin View* (e.g., charts or combined results).
* The selected `item_id` from the `Company` view is passed to the new view dynamically.

This dynamic linking is handled automatically by JCB once the target and placement settings are correctly configured.

---

## **5. Using "Order Before" Options**

The **Order Before** fields are used when your Custom Admin View is added to a **Main Menu** or **Submenu**.

These fields define where your new menu item should appear relative to existing items.
For example:

* If you select *Dashboard (list of records)* as "Order Before", your new view will appear directly before the dashboard link in the admin menu.

This step ensures your admin interface remains logically organized.

---

## **6. Implementing Custom Buttons**

Custom Admin Views often include **custom buttons** that trigger specific actions or navigate to other views.

1. Go to your Custom Admin View (e.g., *Company Results*).
2. Scroll to the **Custom Buttons** section.
3. Define PHP logic for each button as needed (for example: `editCompany`, `gotoCompany`).

These buttons interact with the component's controller logic. You can define whether each button targets a *single item* or operates at a *list level*.

> **Technical Note:**
> JCB generates the PHP code for these buttons in your component. You can inspect the generated code after compiling to understand or adjust the behavior further.

---

## **7. The "Combined Results" Example**

In the *Cost-Benefit Projection* example:

* The **Combined Results** button was added to the toolbar.
* It displays results by combining data from multiple selected items.
* The associated icon (e.g., a gear or chart icon) helps users identify its function quickly.

Inside the **Combined Results** view, additional buttons such as *Dashboard* and *Companies* were added.
These correspond to the actions available *within* that specific view.

> **Remember:**
> Buttons defined **before opening the view** appear in the toolbar.
> Buttons defined **inside the view** appear once the view is opened.

---

## **8. Linking Data Using Dynamic GET and Selected IDs**

When multiple records are selected in a list view, their IDs (`cid`) can be passed to your Custom Admin View dynamically.
This enables data filtering or aggregation based on user selection.

To achieve this:

1. In your Custom Admin View's **Dynamic GET (Data Query)** section, access the selected IDs using PHP:

   ```php
   $input = JFactory::getApplication()->input;
   $ids = $input->get('cid', array(), 'array');
   ```
2. Validate that the user has permission to access this data.
3. Use `$ids` in your SQL query or data model to fetch the relevant dataset.

In JCB, this is typically implemented in the **getListQuery()** method of the model.
You can modify or extend it via the Dynamic GET builder to suit your component's logic.

---

## **9. Testing and Troubleshooting**

If your view or buttons don't appear as expected:

* Reopen the Custom Admin View and double-check placement options.
* Ensure the **Target View** is properly set.
* Recompile the component and install the updated version.
* Inspect the generated PHP code to verify your logic was included.

Experimenting is part of the learning process. Adjust placements and settings, recompile, and observe the behavior in Joomla until everything works as intended.

---

## **10. Menu Structure and Placement Summary**

When compiled:

* **Main Menu** items appear at the top of your component's admin interface.
* **Submenu** items appear on the left-hand side when viewing a specific section.
* **Dashboard (list of records)** items serve as quick-access buttons or reports on the main component page.

Use these strategically to create a clean, user-friendly backend layout for your component.

---

## **Conclusion**

Adding Custom Admin Views in Joomla Component Builder empowers developers to design rich, interactive administrative interfaces. By properly setting menu placement, target views, and dynamic data handling, you can build professional back-end dashboards and management tools without manually writing all the boilerplate code.

---
