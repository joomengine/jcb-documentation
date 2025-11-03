# Reusing Custom Code in Joomla Component Builder (JCB)

## Overview

[00:00:00](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h00m00s)

This tutorial demonstrates how to reuse and manage **custom PHP code** across different parts of your Joomla Component Builder (JCB) projects. It highlights how to centralize your scripts, functions, and helpers for efficiency and maintainability.

JCB includes several powerful features that make it possible to:

* Write generic helper functions once and use them across multiple components.
* Insert reusable code snippets dynamically into component templates.
* Maintain custom logic from a central location instead of editing multiple files.

---

## Scenario: The Need for Code Reuse

[00:00:33](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h00m33s)

A developer (Alex Dings) posed a question on the JCB forum:

> "I have several admin views that share generic code, but some views require specific variations. How can I efficiently maintain this structure?"

### Common Challenges:

* Duplicating PHP helper functions across different admin views.
* Updating multiple component files whenever logic changes.
* Managing both **generic** and **specific** functionality within multiple JCB-generated views.

JCB solves this through **Custom Code Blocks** and **Helper Class Injections**.

---

## Setting Up the JCB Environment

[00:01:12](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h01m12s)

To follow along, use a Joomla test environment. You can quickly spin up a **Docker-based Joomla instance** for testing.

### Steps:

1. Pull a Joomla Docker image:

   ```bash
   docker pull joomla
   docker run -p 8080:80 joomla
   ```
2. Access Joomla at `http://localhost:8080`
3. Log in as an admin and go to:
   **Extensions → Install → Web → Search "JCB"**
4. Install **Joomla Component Builder** from the Joomla Extensions Directory (JED).

[00:02:22](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h02m22s)

Initialise the [repository index](./JCB-Packaging-Engine.md) and use **Init** on the Components view to
import the demo blueprints that ship with JCB. They provide real-world examples of how custom code is
structured inside full projects.

> **Tip:** Always click **Force Local Update** to ensure your local JCB fields and structure are up to date.

Once installed, you can explore JCB's internal components and study its **demo data**.

---

## Understanding Custom Code in JCB

[00:03:00](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h03m00s)

JCB includes a **Custom Code Manager** under:

> **Component → Custom Code**

This area allows you to define reusable code blocks that are injected during compilation. The UI now labels two complementary workflows:

1. **JCB (manual)** – Write a reusable snippet once, inject it anywhere with `[CUSTOMCODE=...]`, and optionally pass arguments that map to `[[[arg0]]]`, `[[[arg1]]]`, etc. Remember to encode reserved characters such as `,` or `+` (`&#44;`, `&#43;`) when sending them as arguments.
2. **Hash (automation)** – Surround code inside a compiled component with insert or replace tags (e.g. `/***[INSERT<>123]***/`) so JCB can import the block, track its location, and reapply it on future builds.

Both types live in the same manager so you can mix reusable helper logic with on-disk overrides without losing the relationship to their target files.

---

## Example 1: Using the `getViewID()` Custom Code

[00:03:40](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h03m40s)

A good example from JCB's demo data is the **`getViewID()`** function.

This function is created as a reusable snippet in **Custom Code** and is applied across multiple **Admin Views**.

### Example Workflow:

1. Open **Custom Code → getViewID**
2. Observe where it is used (e.g., in Admin Views).
3. The snippet might look like:

   ```php
   public static function getViewID($view)
   {
       // Function logic
   }
   ```
4. In your admin view, call the function like:

   ```php
   $id = HelperClass::getViewID('myview');
   ```

[00:04:55](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h04m55s)

If your function includes variables like `vdm`, you can make them dynamic using argument placeholders.

### Passing Arguments to Custom Code

You can replace variables using the **argument placeholder syntax**:

```php
[[[[arg0]]]]
```

Then, pass arguments during use:

* `arg0` → `value1`
* `arg1` → `value2`

This makes your snippets more flexible across different contexts.

---

## Example 2: Helper Function Reuse - `getFilePath()`

[00:05:55](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h05m55s)

The second method of code reuse involves adding functions to your **Helper Classes**.

In JCB, you can define code to be automatically added to:

* **Admin Helper Class**
* **Site Helper Class**
* **Both simultaneously**

### Example:

The `getFilePath()` function can be defined once and reused in multiple components.

```php
public static function getFilePath($file)
{
    // Return the full path to a given file
}
```

[00:06:20](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h06m20s)

In JCB:

1. Open **Custom Code → PHP Helper (Both Admin & Site)**
2. Add your reusable function there.
3. JCB automatically includes this in both helper classes during compilation.

> **Best Practice:** Use the "Both" helper class option when a function applies globally.

You can later view where each custom code block is used at the bottom of its detail page.

---

## Managing Reuse Across Components

[00:07:45](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h07m45s)

Because custom code snippets are tracked centrally in JCB:

* You can easily modify or update them once.
* Any components that use the snippet will get the updated code after recompilation.

This is especially useful for maintaining **shared libraries** of logic that appear in multiple JCB-generated components.

---

## Understanding Automation and IDE-Linked Code

[00:08:28](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h08m28s)

JCB distinguishes between:

* **Hash (Automated) Custom Code:** Managed by JCB and inserted automatically into specific files (linked to IDE edits).
* **Manual Custom Code:** Standalone snippets created for reuse in different parts of components.

### Key Differences:

| Type                 | Purpose               | Control           |
| -------------------- | --------------------- | ----------------- |
| **Automated (Hash)** | One file/one location | IDE-tracked       |
| **Manual (Snippet)** | Multiple uses         | Developer-managed |

> **Note:** Both use the term "Custom Code," but serve distinct purposes. Don't confuse the two when managing snippets.

---

## Summary

[00:09:25](https://www.youtube.com/watch?v=8Yl4lAAAWMQ&t=00h09m25s)

**Custom Code Reuse** is one of the most powerful time-saving tools in Joomla Component Builder.
By properly structuring your reusable logic using:

* **Helper Class injections**, and
* **Manual custom snippets**,

you can dramatically improve efficiency and reduce maintenance overhead.

---

## Key Takeaways

* Use **Custom Code (Manual)** for flexible, multi-use snippets.
* Use **Helper Class (Both)** for reusable logic shared between admin and site areas.
* Use **Automated (Hash)** only for one-off inline code.
* Always **recompile your component** after updating custom code to apply changes.

---
