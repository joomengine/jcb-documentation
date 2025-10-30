# The Custom Dashboard Option in Joomla Component Builder (JCB)

> **Tutorial Reference:** [Video 60 – The Custom Dashboard Option in JCB](https://www.youtube.com/watch?v=tU7TeYn1Djo)
> **Timestamped Transcript Integrated**
> **Updated for:** Latest JCB Version (2025)

---

## Overview

[00:00:00](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h00m00s)

JCB now offers developers the ability to **add their own custom dashboard** to any Joomla component created with it.
This enhancement allows for **greater UI flexibility** and a **unique administrative experience**-no longer limited to the default dashboard layout.

In previous versions of JCB, all components used the same default dashboard. The layout and icons were auto-generated based on your component's configuration. Now, you can **replace or redesign** that dashboard entirely to match your brand or functionality needs.

---

## 1. Default Dashboard Behavior

When you create a new component in JCB without defining a custom dashboard, the system automatically generates one based on your:

* Admin views
* Icons
* Field layouts

This is the **default JCB dashboard** - functional, but not customizable.

> **Tip:** If you don't add your own dashboard, JCB continues to build this default layout for you.

---

## 2. Adding Tabs (Optional)

[00:00:43](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h00m43s)

JCB's default dashboard supports **tabs**, which allow you to structure the admin interface into sections. Tabs are quite powerful, letting you embed lists, stats, or even dynamic content.
However, for many developers, this still looks *"too JCB-like"* and lacks originality.

[00:01:22](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h01m22s)

JCB was designed to help developers **build unique components**, not cookie-cutter ones. If you're comfortable with HTML, CSS, and JavaScript, you can design a completely **custom admin dashboard view**.

> **Tip:** A custom dashboard lets you express your own brand and layout while keeping the same JCB backend logic.

---

## 3. Viewing the Dashboard in the Hello World Component

[00:02:41](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h02m41s)

Let's open the well-known **Hello World component** in JCB as an example.

1. Go to **Components → Hello World** in Joomla.
2. You'll see the default dashboard layout.
3. We'll now remove or replace this dashboard.

---

## 4. Accessing the Dashboard Settings

[00:03:27](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h03m27s)

Inside JCB:

1. Navigate to your component.
2. Open the **"Dash & Install"** tab in the component configuration.
3. You'll find two key options under **Dashboard Type**:

   * **Default** – the standard JCB-generated dashboard.
   * **Dynamic** – allows selecting a custom admin or site view to serve as the new dashboard.

When you select **Dynamic**, JCB displays a list of all available **Admin and Custom Admin Views** associated with your component.

---

## 5. Setting a Custom Dashboard

[00:03:52](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h03m52s)

To change the dashboard:

1. Choose **Dynamic** from the dropdown.
2. Select any available Admin or Custom Admin View (e.g., "Compiler" or "Snippets").
3. Click **Save & Close**.
4. Rebuild your component by opening the **Compiler** in JCB and clicking **Compile**.
5. Install the updated component in Joomla.

[00:04:17](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h04m17s)

After reinstalling:

* The old dashboard disappears.
* The selected view (for example, a list view) becomes the **default admin landing page**.

> **Result:** Your Hello World component now opens directly into the chosen view instead of the default dashboard.

---

## 6. Using a Custom Dashboard (Example: JCB Compiler View)

[00:04:34](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h04m34s)

Let's test this feature using JCB itself.

JCB has several **Custom Admin Views**, such as:

* **Compiler**
* **Snippets**
* **Fields**
* **Layouts**

To assign one as the dashboard:

1. Open JCB's component configuration.
2. In **Dash & Install**, select **Dynamic**.
3. Choose one of the views (for example, "Compiler").
4. Click **Save & Close**.
5. Recompile and reinstall JCB.

---

### Testing the Custom Dashboard

[00:05:20](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h05m20s)

After recompiling:

* JCB's dashboard is replaced by the **Compiler view**.
* Some dashboard elements (like version info, tabs, and updates) are no longer available - because the dashboard files were removed.

If you refresh the admin page:

* The new **Compiler dashboard** appears as the landing screen.
* All previous dashboard code and files are deleted from the build.

[00:06:23](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h06m23s)

The change is **clean and complete** - no residual dashboard files remain in the component structure.

---

## 7. Reverting to the Default Dashboard

[00:07:17](https://www.youtube.com/watch?v=tU7TeYn1Djo&t=00h07m17s)

To restore the original dashboard:

1. Reopen the component in JCB.
2. In **Dash & Install**, set the dashboard type back to **Default**.
3. Click **Save & Close**.
4. Compile and reinstall the component.

Once done:

* The original JCB dashboard is restored.
* All dashboard files are re-added automatically.

> 💡 **Tip:** Switching between dashboards doesn't harm your component.
> You can safely experiment with different layouts or restore defaults anytime.

---

## 8. Why Use a Custom Dashboard?

Creating a custom dashboard gives your component a **distinct identity** and better **user experience**.

You can design dashboards that:

* Display **custom data summaries**
* Integrate **graphs, charts, or stats**
* Provide **quick access buttons**
* Embed **custom HTML, JavaScript, or modules**

> **Example Use Cases:**
>
> * A sales management component could display revenue stats or sales charts.
> * A content builder might show quick actions to create or publish items.

---

## 9. Summary

| Feature               | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| **Default Dashboard** | Auto-generated by JCB with standard layout and tabs.                  |
| **Dynamic Dashboard** | Lets you assign a custom Admin or Custom Admin View as the dashboard. |
| **Compile & Install** | Required after making changes to reflect them in Joomla.              |
| **Revert Option**     | Switch back to default anytime without loss of data or structure.     |

---

### Final Thoughts

The **Custom Dashboard** feature is a major step toward flexibility in JCB.
You now have the power to make your component's backend truly **your own** - blending JCB's automation with your design creativity.
