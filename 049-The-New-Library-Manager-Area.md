# Managing Libraries Dynamically in JCB

[00:00:00](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

This tutorial explains the new **Library Manager** area in Joomla Component Builder (JCB), which introduces a dynamic, flexible, and centralized way to manage JavaScript and CSS libraries such as Bootstrap, UiKit, and FooTable. The improved implementation simplifies how libraries are added and linked to components and views.

---

## 1. Understanding Libraries in JCB

Libraries are external frameworks or tools that enhance your Joomla components.
Previously, JCB supported three prebuilt libraries-**UiKit**, **FooTable**, and **No Library**-that could be toggled via the "Add UiKit" and "Add FooTable" options in the component settings.

Now, with the **Library Manager**, libraries are handled dynamically and linked directly to specific **views**, allowing for greater flexibility and reuse across components.

---

## 2. How It Used to Work

[00:00:53](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m53s)

In earlier versions, libraries were added globally within the component settings.
For example, developers could choose to include UiKit or FooTable globally and specify preferred versions.

However, this method was limited. Adding a new library required creating a folder in:

```
administrator/components/com_componentbuilder/custom/
```

You would then manually place the library files (for example, Bootstrap) inside a custom folder and refresh the component's configuration. These files were then copied to the media directory when compiling.

This approach worked but required manual configuration and duplicated effort for each component.

---

## 3. Introducing the Dynamic Library Feature

[00:01:34](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m34s)

The new **Dynamic** option changes how libraries are managed.
Instead of globally assigning libraries to all components, you can now link libraries directly to **specific views**.

By setting a library to *Dynamic*, the global inclusion is turned off, and JCB automatically determines which libraries are required based on the views linked to the component.

---

## 4. The Library Manager Interface

[00:05:43](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

Open the **Libraries** section in JCB.
You'll find several predefined libraries:

* **Bootstrap 4**
* **UiKit 2**
* **UiKit 3**
* **FooTable 2**
* **FooTable 3**
* **No Library**

These base libraries should not have their *names* or *types* changed, but their **behavior** and file sources can be configured.

---

## 5. Configuring Library Behavior

[00:06:44](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m44s)

Each library has configurable **File Behaviors** that control how its assets are added:

* **Always Add** – always include these files.
* **Local (Get)** – download and include files locally during compilation.
* **Conditions** – include files only when specific conditions are met (under development).
* **Custom Script** – write your own PHP logic to include files dynamically.
* **Do Not Add** – exclude files completely.

You can switch between CDN links and local files by changing the **Type** field from "Link" to "Local."
When compiling, JCB downloads and embeds the necessary files automatically.

---

## 6. Adding Files and Folders to Libraries

[00:07:32](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h07m32s)

Files can be added from the same **Custom Files and Folders** area used in older JCB versions, but now this is managed **per Library** instead of per Component.
Once configured, these files are automatically included in all views linked to that library, ensuring consistency and saving time.

---

## 7. Using Configuration Fields and Conditions

[00:09:17](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m17s)

Conditions are currently being developed, but their purpose is to allow selective inclusion of files based on **component configuration fields**.

You can:

1. Create custom configuration fields in JCB.
2. Link them to a library using "Library Config."
3. Use those fields to toggle specific files dynamically during runtime.

For example, a "Use Bootstrap" radio field could determine whether Bootstrap scripts are added to the page.

---

## 8. Writing Custom Scripts

[00:12:10](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h12m10s)

The **Custom Script** behavior allows you to define how and when library files load using PHP.
For example, you can replace component names dynamically or adjust file paths during compilation.

When JCB compiles the component, it automatically detects `.css` and `.js` file types and places them in the correct directories.

This gives developers full control to write logic-driven inclusions and extend library functionality beyond static linking.

---

## 9. Linking Libraries to Views

[00:14:50](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m50s)

To use a library in your component:

1. Go to **Site Views**.
2. Open a specific view (e.g., "Looks").
3. Select a library such as **Bootstrap v4** from the Library dropdown.

Once selected, JCB filters the available **Snippets** to match that library.
This ensures that only relevant snippets (like Bootstrap alerts) are available for insertion.

---

## 10. Installing Library Snippets

[00:15:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m19s)

You can import snippets for each library directly from the community:

1. Click **Get Snippets**.
2. Choose a library (e.g., Bootstrap v4).
3. Import snippets individually or use **Get All New Snippets** to bulk import all available snippets.

Installed snippets will then appear under that library's Snippets list, ready for use in your views.

---

## 11. Creating Library Bundles

[00:18:04](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m04s)

When you need to use multiple libraries together (for example, UiKit 2 and UiKit 3), create a **Bundle**:

1. Click **New** in the Library Manager.
2. Choose **Bundle** as the type.
3. Select the libraries to include (e.g., UiKit 2 and UiKit 3).
4. Add any custom configuration or scripting as needed.
5. Save the bundle.

This allows a single bundle to load multiple libraries conditionally or simultaneously, depending on your script logic.

---

## 12. Using Custom Script Behavior with Bundles

[00:21:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h21m19s)

In a bundle, you can write PHP-based logic using component parameters to determine which library files load.
These parameters are accessed via `$this->params` in the PHP code.
You can check parameter values and conditionally include files based on configuration fields.

This allows complex scenarios-such as switching between UiKit versions or loading Bootstrap only under certain component options.

---

## 13. Compiling Components with Linked Libraries

[00:27:02](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h27m02s)

When you compile your component, JCB automatically:

* Downloads any files marked as **Local (Get)**.
* Inserts file paths correctly in your component code.
* Adds library references to views and layouts that have been linked.

You can verify the output by checking the compiled `/media/com_yourcomponent/` directory.

---

## 14. Linking Libraries to Views, Templates, and Layouts

[00:28:15](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h28m15s)

To ensure a library is available in a specific context, you must explicitly link it to that:

* **Site View**
* **Custom Admin View**
* **Template**
* **Layout**

Each view or layout can have multiple libraries attached, or even a bundle, depending on your design requirements.

---

## 15. Compatibility with Older Implementations

[00:29:01](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h29m01s)

The older library implementation in **Libs & Helpers** still works for backward compatibility.
If you set a component to "Add UiKit 2 and 3" or "Add FooTable 2," JCB continues to handle them globally.
However, the **Dynamic** method is recommended for new components as it gives you finer control and better scalability.

---

## 16. Conclusion

[00:30:19](https://www.youtube.com/watch?v=rDjvgLYOt1o&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h30m19s)

The **Library Manager** in JCB provides a robust, modular way to manage external libraries.
You can now:

* Link libraries directly to views.
* Define custom behaviors or conditions.
* Create reusable bundles.
* Import and share snippets through the community.

This dynamic system reduces duplication, simplifies maintenance, and enhances flexibility in Joomla component development.

---
