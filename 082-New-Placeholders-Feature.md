# New Placeholders Feature in Joomla Component Builder

---

## Introduction

*(Timestamp: [00:00:00](https://www.youtube.com/watch?v=USVLYu4ZLCc&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m26s))*

In **JCB version 2.9.14**, a new feature was introduced: **Global and Component-Level Placeholders**.
This feature allows you to define and reuse placeholders dynamically across your components - enhancing flexibility, reusability, and maintainability of your generated Joomla code.

Before diving into the new functionality, it's important to understand JCB's existing placeholders system.

---

## Existing (Core) Placeholders

### 1. Component-Level Placeholders

*(Timestamp: [00:00:26](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h00m26s))*

JCB already includes a set of **default placeholders** that you can use throughout the system.
Examples include:

* `[[[component]]]` - Lowercase component name
* `[[[Component]]]` - Capitalized first letter
* `[[[COMPONENT]]]` - Uppercase
* `###component###` - Wrapped in hashes
* `<<<component>>>` - Wrapped in angle brackets

These placeholders are automatically replaced during compilation with the relevant component name in the correct format.

---

### 2. View-Level Placeholders

*(Timestamp: [00:02:02](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h02m02s))*

Similarly, **views** have their own set of placeholders. Depending on where they're used (admin or site), they vary slightly.

Common forms include:

* `[[[view]]]`, `[[[View]]]`, `[[[VIEW]]]`
* `###view###`
* `[[[views]]]` - for list views (plural)

**Note:**

* In the backend (admin area), placeholders such as `view` and `views` correspond to **list** and **edit** views.
* In the site area, the view placeholders begin with a lowercase or uppercase **S** (e.g., `[[[SView]]]`), representing the site context.

---

## Introduction of Custom Placeholders

*(Timestamp: [00:04:36](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h04m36s))*

The new **Placeholder Manager** in JCB allows you to define **your own placeholders** within the GUI, giving developers the same flexibility as custom code snippets - but for **text strings** instead of code.

Unlike custom code:

* Placeholders do **not** use an IDE-style editor.
* They perform **in-place string replacement** during compilation.
* They can be applied globally or overridden per component.

---

## Using the Placeholder Manager

*(Timestamp: [00:05:03](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h05m03s))*

### Accessing the Manager

1. In JCB, navigate to **Placeholders** in the admin menu.
2. You'll see a list of existing placeholders. If you've imported components, some may already be defined; otherwise, the list will be empty.

### Creating a New Placeholder

*(Timestamp: [00:05:29](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h05m29s))*

1. Click **New** to create a new placeholder.

2. Enter a **name** - JCB will automatically enclose it in triple square brackets, e.g.:

   ```
   [[[MyPlaceholder]]]
   ```

3. In the **Value** field, enter the string or variable you want to substitute.

   * The value can include:

     * Dollar signs (`$`)
     * Brackets (`[ ]`), braces (`{ }`)
     * Any single-line string
   * Example:

     ```
     $myVariableName
     ```

4. JCB automatically searches across all components to detect if this placeholder is already in use.

5. Click **Save & Close** to finalize.

> **Tip:**
> If your placeholder's value causes errors (for example, due to special characters), report it on GitHub - placeholders are designed to handle nearly all valid string patterns.

---

## Using Custom Placeholders in Components

*(Timestamp: [00:08:26](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h08m26s))*

Once a placeholder is created, it can be inserted in multiple areas - helper classes, custom code snippets, or dynamic GET methods.

### Example: Adding a Placeholder to a Helper Class

1. Open a component (e.g., `Anthropometry`).
2. Add your placeholder to the **Helper Class**.

   ```php
   [[[AnyWord]]]
   ```
3. Save and close.

You can reuse the same placeholder in another component (e.g., `MedicalAid`).

This allows shared logic or code snippets to dynamically adjust based on component-level overrides.

---

## Advanced Example: Combining with Custom Code

*(Timestamp: [00:09:17](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h09m17s))*

Consider a reusable **custom code snippet** like a JavaScript loader animation (`Little Dot Trick`).
If multiple components use this same snippet but require slightly different text or behavior, you can insert placeholders inside it:

```javascript
console.log("[[[AnyWord]]]");
```

Then, for each component:

* Override the placeholder in **Component → Placeholders**:

  * For one component: `[[[AnyWord]]] = "not like the other"`
  * For another: `[[[AnyWord]]] = "default string"`

During compilation, JCB replaces these dynamically - ensuring component-specific variations without duplicating code.

---

## Compiling and Verifying

*(Timestamp: [00:12:43](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h12m43s))*

After setting placeholders:

1. Compile your components (e.g., `Anthropometry`, `Medical Aid`).
2. Install them into your Joomla site.
3. Open the compiled **helper class** or **custom code snippet** in the IDE.
4. Verify that the placeholders were replaced with the correct component-level or global values.

Example:

* In `AnthropometryHelper`, `[[[AnyWord]]]` → "not like the other"
* In `MedicalAidHelper`, `[[[AnyWord]]]` → global string

This confirms successful context-aware replacement.

---

## Key Benefits of the Placeholder System

*(Timestamp: [00:15:09](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h15m09s))*

* **Dynamic Reusability** – Write one snippet of code or string logic, reuse it across components with unique contextual differences.
* **Simplified Maintenance** – Centralize updates; one placeholder definition updates everywhere it's used.
* **Component-Level Overrides** – Different behavior for the same placeholder across components.
* **Seamless Integration** – Works within helpers, custom code, dynamic GET, or any JCB text area.
* **Cross-Component Compatibility** – Perfect for large projects with interdependent components (e.g., the "Coral" core project example).

---

## Conclusion

*(Timestamp: [00:16:48](https://www.youtube.com/watch?v=USVLYu4ZLCc&t=00h16m48s))*

The **New Placeholder Feature** represents a major step forward in JCB's evolution.
It empowers developers to:

* Write cleaner, more maintainable code,
* Reuse snippets effectively across components, and
* Dynamically adjust text or code values based on context.

As JCB continues to evolve, placeholders will play a key role in improving component interoperability and developer productivity.
