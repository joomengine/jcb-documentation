# Add or Remove Prefix to Component Name in Joomla Menu

This tutorial explains the new Joomla Component Builder (JCB) feature that allows developers to **add or remove a prefix** from the component name displayed in the Joomla menu. This customization helps you brand or visually distinguish your component entries within the Joomla admin interface.

---

## 1. Understanding the Menu Prefix

[00:00:00](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

In earlier versions of JCB, components automatically included a prefix symbol (like a small arrow) before their name in the Joomla admin menu. For example, your component might appear as:

```
➤ Component Builder
```

With the new feature, you can now **customize or remove this prefix** entirely.

---

## 2. Accessing the Global Configuration

[00:00:26](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m26s)

1. In JCB, open your component.
2. Navigate to the **Global** tab within the component's configuration.
3. Look for the **Add Menu Prefix** setting.

Here, you can:

* Set **"No"** to remove the prefix completely.
* Enter a **custom prefix** string or symbol.
* Leave the field as-is to use the **default arrow (›)**.

> **Tip:** You do not need to manually add a space after the prefix — JCB automatically includes one.

---

## 3. Using HTML Character Entities for Symbols

[00:00:56](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m56s)

Because the prefix is stored in an XML file, any special or non-standard characters must be represented as **HTML character entities**.

For example:

* `&#9658;` → ►
* `&#10003;` → ✓
* `&#8857;` → ⊙

You can find a full list of HTML entities here:
[HTML Character Entities Reference (w3schools.com)](https://www.w3schools.com/html/html_entities.asp)

You may also use your **company name** or a short **text prefix** instead of a symbol. For instance:

```
JCB MyComponent
```

---

## 4. Example: Changing the Prefix Symbol

[00:01:36](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m36s)

To demonstrate, let's change the prefix to a small circle symbol:

1. Copy the HTML entity:

   ```
   &#8857;
   ```
2. Paste it into the **Add Menu Prefix** field.
3. Click **Save & Close**.
4. Compile one of your demo components.
5. Install the compiled package in Joomla.

**Result:**
The component name in the Joomla menu now appears as:

```
⊙ Demo
```

---

## 5. Removing the Prefix Entirely

[00:02:45](https://www.youtube.com/watch?v=vwZyhKp_L38&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m45s)

If you prefer a clean menu name without any prefix:

1. Set **Add Menu Prefix** to **No**.
2. Save your settings.
3. Recompile and install your component.

Now, the component will appear simply as:

```
Demo
```

---

## 6. Summary

| Action            | Setting              | Result                                             |
| ----------------- | -------------------- | -------------------------------------------------- |
| Add custom symbol | `&#8857;` or similar | Displays a custom prefix before the component name |
| Remove prefix     | Set to **No**        | Displays the component name only                   |
| Use company name  | e.g. `MyCo`          | Adds branding before the component name            |

---

### Helpful Tips

* Always use **valid HTML entities** for symbols to avoid XML errors during compile.
* You can modify this setting anytime without affecting other parts of your component.
* Recompile and reinstall the component after each change to see updates in the Joomla menu.

---
