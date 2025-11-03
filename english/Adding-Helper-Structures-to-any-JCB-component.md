# Adding Helper Structures to Any JCB Component

This guide walks you through the process of integrating **Helper Structures**-such as help documentation-into any Joomla Component Builder (JCB) component.
It is based on the official tutorial video *"Adding Helper Structures to Any JCB Component"* and expanded for clarity, accuracy, and completeness.

---

## 1. Introduction to Helper Structures

**[00:00:00](https://www.youtube.com/watch?v=nw9YPu9emws&t=0s)**

A question arose about how to integrate a **Help Menu** into JCB components. JCB includes a **Help Document** area that allows developers to provide documentation and contextual assistance within their components.

Although time did not allow for an in-depth expansion of this feature in the video, the **Help Document system** can be easily added to any JCB component through a helper structure.

---

## 2. Obtaining the Sermon Distributor Package

**[00:00:39](https://www.youtube.com/watch?v=nw9YPu9emws&t=39s)**

To follow along with this demonstration, the **Sermon Distributor Package** is required.
This package includes preconfigured structures, such as the **Help Document Admin View**, which can be imported into any component.

1. Visit the VDM.io GitHub repository:
   `https://github.com/vdm-io/JCB-Packages`
2. Locate the **Sermon Distributor** package.
3. Purchase the activation key from [http://vdm.bz/jcb-packages](http://vdm.bz/jcb-packages).

Once installed, all necessary data and instructions are included in the package documentation.

---

## 3. Adding the Help Document Admin View

**[00:02:48](https://www.youtube.com/watch?v=nw9YPu9emws&t=168s)**

1. Open your demo component in JCB.
   For example: `com_demo`.
2. Go to **Admin Views** and click **+** to create a new view.
3. Name the view **Help Document**.
4. Assign the **Support** icon.
5. Configure the following options:

   * **Metadata:** *Not required*
   * **Access:** *Not used*
   * **Import:** *Optional*
   * **Frontend Editing:** *Disabled*
   * **Menu Position:** *Second position (optional)*

> **Tip:** If tick-box issues appear (fields not showing correctly), simply close and reopen the form.
> JCB is phasing out repeatable fields in favor of **subforms**, which provide better flexibility and database consistency.

Save and close the new Admin View.

---

## 4. Compiling and Installing the Updated Component

**[00:04:52](https://www.youtube.com/watch?v=nw9YPu9emws&t=292s)**

1. Navigate to **Compiler**.
2. Compile your demo component (`com_demo`).
3. Install the newly compiled ZIP file through Joomla's **Extension Manager**.

> Ensure that the component is **not already installed** before compiling; otherwise, database conflicts may occur.

After installation, open the Demo Component and verify that a new **Help Documents** area has been added.

---

## 5. Creating a New Help Document

**[00:05:43](https://www.youtube.com/watch?v=nw9YPu9emws&t=343s)**

1. Go to **Help Documents** and click **New**.
2. Set the **Target Group** to *All*.
3. Under **Location**, select an Admin Area view (e.g., Dashboard or Looks).
4. Provide a **Title** and select the **Type of Help**.

### Help Types

#### a. External URL

**[00:06:41](https://www.youtube.com/watch?v=nw9YPu9emws&t=401s)**
Use this when distributing a component publicly.
This links the help content to an **external page** (such as documentation or video tutorials) that can be updated without shipping a new component version.

#### b. Text

**[00:07:20](https://www.youtube.com/watch?v=nw9YPu9emws&t=440s)**
For simple, internal help content, choose **Text** and enter the instructions directly.
Example:

> "This is the help you need."

Save and close the record.

Once saved, the targeted view (e.g., **Looks**) will display a new **Help** button, which opens the content or link in a modal.

---

## 6. Targeting Additional Views

**[00:08:32](https://www.youtube.com/watch?v=nw9YPu9emws&t=512s)**

You can target either:

* **List views** (plural, e.g., Looks)
* **Edit views** (singular, e.g., Look)
* **Frontend views** (site area)

Each can have unique help content linked to different URLs or text.

---

## 7. Linking Help Documents to Database Tables

**[00:09:36](https://www.youtube.com/watch?v=nw9YPu9emws&t=576s)**

To ship your component with built-in help content:

1. Go to **Admin Views → Help Document**.
2. Assign a **System Name**, e.g., `demo_help_document`.
3. Add a **MySQL Table Link**:

   * Enable *Linked to MySQL Table*: Yes
   * Choose Source: *Table*
   * Select `demo_help_document`
   * Remove unnecessary fields (as demonstrated in the video).

Save and close.

> **Important:** Always compile the component **before uninstalling** the local version.

---

## 8. Understanding the SQL Insert Process

**[00:11:57](https://www.youtube.com/watch?v=nw9YPu9emws&t=717s)**

When you compile the component:

* The file `install.mysql.utf8.sql` will automatically include:

  * Table creation code
  * `INSERT` statements for the default Help Document records

This means that help data (like links and text) will be added to the database upon component installation.

> Note: These inserts are **not included in update files**.
> For updates, use **custom scripting** in the JCB PHP tab under *Install / Update / Uninstall Events* to reinsert data.

---

## 9. Handling Missing Linked Tables

**[00:13:48](https://www.youtube.com/watch?v=nw9YPu9emws&t=828s)**

If you uninstall the component and then attempt to recompile it, you may encounter the error:

> `An error has occurred: Table 'demo.#_demo_help_document' doesn't exist`

This happens because the linked table no longer exists.
To resolve this:

1. Return to the **Admin View**.
2. Change the MySQL Source from **Table** to **Dump**.
3. Copy the SQL from your dump file and paste it into the MySQL field.

Now you can compile the component successfully even if it is uninstalled.

---

## 10. Verifying the Dump File

**[00:16:04](https://www.youtube.com/watch?v=nw9YPu9emws&t=964s)**

After recompiling, open the new ZIP file and check the `install.mysql.utf8.sql` file.
You'll see that your **Dump Data** has been properly inserted, confirming that the Help Document data is now hardcoded into the install script.

---

## 11. About the Sermon Distributor Helper Script

**[00:16:45](https://www.youtube.com/watch?v=nw9YPu9emws&t=1005s)**

You can create your own Help Document structure from scratch without purchasing the Sermon Distributor package.
However, that package includes **custom PHP scripting** that automates adaptation of the help structure for any component - a good reference for advanced users.

---

## 12. How JCB Detects Help Documents

**[00:17:51](https://www.youtube.com/watch?v=nw9YPu9emws&t=1071s)**

When JCB detects that a view is a **Help Document** and the appropriate fields are set, it automatically:

* Builds the front-end and back-end behaviors
* Integrates the contextual help buttons
* Supports dynamic linking between admin and site views

This allows users of your component to modify or extend help content according to their needs.

---

## 13. Summary

**[00:18:59](https://www.youtube.com/watch?v=nw9YPu9emws&t=1139s)**

You have now learned how to:

1. Add a **Help Document Admin View** to any component.
2. Configure and target help entries to specific views.
3. Link help data to your component's database.
4. Use **Dump** mode to preserve data for compilation.
5. Understand how JCB auto-detects and integrates help structures.

This process makes your components more **user-friendly** and **self-documented**, reducing support requests and improving the user experience.

---
