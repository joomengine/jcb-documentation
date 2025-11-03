# Join Fields in the Admin List View with Field Relations

## Introduction

[00:00:00](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

Joomla Component Builder (JCB) version **2.8** introduced a powerful new feature: **Field Relations** for joining fields directly within the **Admin List View**.
This allows you to **combine multiple field values into a single display column** while keeping the ability to **filter and search** using those same fields.

> If you've used **custom scripting** in your component list views before upgrading, note that the new build structure may affect your custom code placement. After upgrading, review and reinsert any custom code snippets where needed.

---

## What the Feature Does

[00:01:27](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m27s)

The **Admin Field Relations** feature lets you **join multiple field values** into one combined display column.
For example, you can combine a **preacher's name**, **email**, and **website** into a single list entry that shows whichever field has a value - while still keeping filtering and linking functionality intact.

### Example Scenario

Using the *Sermon Distributor* component, you may want your Preachers list to display:

* **Name**
* **Email (if present)**, or
* **Website (if no email)**

All in one column beside the preacher's name.

---

## Creating an Admin Field Relation

[00:02:35](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m35s)

1. Open **Component Builder → Admin Views**.
2. Choose your target admin view (e.g., *Preachers*).
3. Scroll to the **Fields** area.
4. At the bottom, click **"Create admin fields relations for this admin view"**.
5. You'll be taken to the **Admin Fields Relations Builder**.

Here you can define how the fields should be joined and in which area the relation will act.

---

## Understanding the "Area" Column

[00:03:43](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h03m43s)

The **Area** setting determines where your relation logic applies:

* **Model (Before Modelling):** modify data before JCB processes it.
* **Model (After Modelling):** modify data after JCB structures it.
* **View:** modify or combine the generated HTML output.

If you need to modify raw values (e.g., plain text or numbers), use **Model**.
If you want to manipulate how the HTML renders, use **View**.

---

## Example: Targeting the Model Area

[00:06:52](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m52s)

1. In the **Admin Field Relations Builder**, choose your **Name** field.
2. Add **Email** and **Website** as the joined fields.
3. Set **Area** to **Model**.
4. Choose **Joint Type: Concatenation**.
5. Under **Glue**, specify what separates the values (e.g., comma, arrow, or space).

When compiled, the joined output appears in the list view like this:

```
John Doe, johndoe@example.com
```

You can customize the glue or use PHP logic for dynamic behavior.

---

## Using PHP Code in Relations

[00:09:32](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m32s)

You can replace the glue option with **custom PHP code** by selecting the **"Code"** type.
JCB uses field IDs wrapped in curly braces `{}` to reference fields (e.g., `{1222}` for email, `{280}` for website).

Example PHP snippet:

```php
if (!empty($item->{1222})) {
    $details = $item->{1222};
} elseif (!empty($item->{280})) {
    $details = $item->{280};
} else {
    $details = '';
}
```

> **Tip:** Once you confirm which field IDs map to which values, remove JCB's generated comments for cleaner output.

You can use any valid PHP logic or even call functions for advanced behavior.

---

## Limitation: One Target per List Field

[00:13:28](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h13m28s)

Each list field can only be targeted **once** in the Field Relations.
If you attempt to use the same field multiple times, only one relation will apply.

---

## Testing the Output

[00:14:44](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h14m44s)

After compiling and installing your component:

* Records with an email display the **email**.
* Records without an email display the **website**.
* Records with neither show a blank entry.

---

## Targeting the View Area

[00:15:53](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h15m53s)

When **Area** is set to **View**, you're joining the **HTML code blocks** JCB builds for each field, not the raw database values.

Example placeholders:

```
[field=199]
[field=1222]
[field=280]
```

These placeholders represent full HTML blocks for each field (including links, permissions, and formatting).
You can combine them, remove unnecessary comments, and even insert HTML tags or PHP as needed.

---

## Example: Concatenation in View Area

[00:18:32](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h18m32s)

1. Use the **Concatenation** joint type.
2. Set the glue to `<br/>` to separate each value on a new line.
3. Compile and install.

Now, your list view displays:

```
Leonard Ravenhill
leonard@example.com
ravenhill.org
```

Each field's HTML (links, permissions, etc.) is preserved.

---

## Advanced Demonstration: Combining Linked Fields

[00:22:15](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h22m15s)

You can join **related table fields** (like Preacher and Sermon) while keeping both links active.

Steps:

1. In the **Sermons Admin View**, open **Fields**.
2. Remove *Preacher* from "Show in List View" but keep it as a **Filter** and **Link**.
3. Go to **Field Relations → New Relation**.
4. Choose:

   * **List Field:** Name
   * **Join Field:** Preacher
   * **Area:** View
   * **Glue:** Space
5. Compile and install.

The list view now shows:

```
Ten Shekels and a Shirt  Paris Reidhead
```

Both values remain clickable, linking to their respective views.

---

## How It Works in the Code

[00:26:16](https://www.youtube.com/watch?v=hh4IIPmYIY8&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h26m16s)

In the model:

```php
$query->select($db->quoteName('a.name'));
$query->select($db->quoteName('preacher.name', 'preacher_name'));
```

In the view:

```php
<?php echo $this->escape($item->preacher_name); ?>
```

JCB automatically handles:

* Table joins
* Permission checks
* Link generation
* Proper escaping and rendering

---

## Best Practices and Tips

* **Always test** your joined fields after compilation and installation.
* **Use "View"** area when you want to preserve HTML and links.
* **Use "Model"** area for manipulating raw values or adding PHP logic.
* **Don't reuse a target field** more than once per view.
* **Keep track of field IDs** when writing custom code.
* **Use JCB's GitHub issues** to report unexpected behaviors.

---

## Summary

This feature simplifies what previously required custom PHP manipulation.
Now, you can easily **join multiple fields in admin list views** using JCB's GUI while keeping full control over filtering, linking, and display logic.

It's a major quality-of-life improvement for developers creating advanced Joomla components with dynamic, readable, and powerful list views.

---
