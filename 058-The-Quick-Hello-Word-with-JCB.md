# The Quick Hello World with Joomla Component Builder (JCB)

## Overview

This quick tutorial demonstrates how to **install**, **import**, **compile**, and **publish** a simple *Hello World* component using Joomla Component Builder (JCB).
It's a streamlined version of the full tutorial, guiding you through setup and execution in just a few minutes.

---

## 1. Installing JCB

**[00:00:00](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h00m00s)**

Before creating any Joomla component, ensure JCB is installed.

1. In your Joomla Administrator, go to:
   **Extensions → Install**
2. Search for **JCB (Joomla Component Builder)**.
3. Select **Install** to start the installation.
   When prompted, confirm any dependency installations.

**Tip:**
If JCB is already installed, you can update it from the same menu to ensure you have the latest version.

---

## 2. Importing the Hello World Package

**[00:00:37](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h00m37s)**

Once JCB is installed, the next step is to import the prebuilt "Hello World" package.

1. In the Joomla Administrator menu, navigate to:
   **Components → Component Builder → Import JCB Packages**
2. Select the **VDM Packages** tab.
3. Locate the **Hello World Component (Free)** package.
4. Click **Get Package**.
   The system will perform a checksum validation such as:

   ```
   4134e94.....
   ```

**[00:01:06](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h01m06s)**
5. Confirm the key matches the one published on **GitHub** to ensure authenticity.
6. Choose **Yes, Force Local Update** and click **Continue**.

When successful, you'll see:

> "Import was successful."

---

## 3. Compiling the Hello World Component

**[00:01:35](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h01m35s)**

Now that the package is imported, it's ready to be compiled into a Joomla component.

1. Navigate to:
   **Components → Component Builder → Compiler**

2. Select **Hello World** from the list.

3. Click **Compile**.
   Once the process completes, you should see a success message.

4. After compiling, click **Install** to install it directly into Joomla.

---

## 4. Testing the Component in the Backend

**[00:02:02](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h02m02s)**

After installation:

1. Go to:
   **Components → Hello World**
2. Create a new greeting record by clicking **New**.
3. In the greeting field, type:

   ```
   Hi James
   ```
4. Click **Save & Close**.

This creates your first "Hello World" entry in the Joomla backend.

---

## 5. Displaying the Greeting on the Frontend

**[00:02:37](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h02m37s)**

To display your greeting:

1. Go to:
   **Menus → Main Menu → Add New Menu Item**
2. For **Menu Item Type**, select:
   **Hello World → Greetings**
3. Save and close the menu item.

Visit your website frontend.
If you encounter a "Page not redirecting properly" error, it's likely due to **permission settings**.

---

## 6. Adjusting Frontend Permissions

**[00:03:02](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h03m02s)**

To make the greeting publicly accessible:

1. Go back to the Joomla Administrator panel.
2. Navigate to:
   **Components → Hello World → Options → Permissions**
3. Under the **Site** section, find:

   * **Greetings**
   * **Allowed**

Set them to **Public → Allowed**.
Click **Save & Close**.

Now refresh your frontend page — your greeting ("Hi James") will appear.
Click on it to open and view the greeting message.

---

## 7. Configuring Edit Permissions (Optional)

**[00:03:29](https://www.youtube.com/watch?v=MEKs1c7LfO8&t=00h03m29s)**

If you try to edit a greeting from the frontend and see *"Not allowed to edit"*, update permissions:

1. Return to **Options → Permissions** in the Hello World component.
2. Under **Edit**, set **Public → Allowed** if desired (for testing only).
   In production, it's recommended to restrict this to logged-in users.

---

## 8. Verifying Functionality

At this point, your Hello World component is fully operational:

* Backend CRUD (Create, Read, Update, Delete) functions work.
* Frontend display is active.
* Permissions are properly configured.

You've successfully installed, compiled, and tested a Joomla component using JCB — all within minutes.

---

## Key Takeaways

* **JCB Packages** simplify the import of preconfigured components.
* **Checksum validation** ensures package authenticity.
* **Compiler** automates generation and installation of Joomla components.
* **Permissions** must be configured for frontend access.

---

## Next Steps

From here, you can begin customizing your Hello World component:

* Add more fields to the Greeting view (e.g., *author*, *date*, *message type*).
* Use **Dynamic GET Builder** to connect other components or filter greetings dynamically.
* Experiment with **admin and site views** to control layout and data flow.

---

**Conclusion:**
The "Quick Hello World" is an essential first step to understanding JCB's workflow — from importing a package to deploying it live.
With these steps mastered, you're ready to build and customize your own Joomla components confidently.
