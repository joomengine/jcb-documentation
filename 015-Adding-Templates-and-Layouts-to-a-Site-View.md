# **Adding Templates and Layouts to a Site View**

### Understanding the Relationship Between Templates and Layouts

[00:00:00](https://www.youtube.com/watch?v=6VBbi3Rl2eY&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)
(*Click the timestamp to open the video in YouTube.*)

After adding a **Dynamic Get** to a Site View, it's essential to understand how **templates** and **layouts** integrate with these views. This helps you know where each piece of code resides, how Joomla loads it, and how JCB structures them during component compilation.

---

## **1. Exploring Templates in a Site View**

### Example: *Preacher View*

[00:00:33](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h00m33s)

In the **Sermon Distributor** example (`/components/com_sermondistributor/views/preacher/tmpl/`), you will find multiple PHP files, such as:

```
default.php
default_preacherbox.php
default_preacherpanel.php
default_preachersmall.php
```

[00:00:58](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h00m58s)

Each of these is a **template**, and they are recognized as such because of how they are included within the default file.

---

### **The Default File - The Site View Core**

[00:01:18](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h01m18s)

The `default.php` file is the main file for the site view - essentially **the view's entry point**.
Inside this file, templates are loaded and rendered.
When you open the **Site View editor in JCB**, the code shown there corresponds directly to the contents of this default file.

---

### **Locating Template Snippets in JCB**

[00:01:50](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h01m50s)

At the bottom of a Site View in JCB, you'll find the **template snippet calls**, such as:

```php
$this->loadTemplate('preacherpanel');
```

[00:02:19](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h02m19s)

You may see template options like:

```
preacher, grid, list, table, panel, box, small
```

These snippets reference the associated template files that JCB compiles into your component.

---

### **Switching Between PHP and HTML in Templates**

[00:02:37](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h02m37s)

Templates can mix PHP and HTML. For example:

```php
<?php if ($this->preacher) : ?>
    <div class="uk-card uk-card-default">
        <?php echo $this->preacher->name; ?>
    </div>
<?php endif; ?>
```

[00:03:04](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h03m04s)

This structure allows you to alternate between PHP and HTML blocks as needed for clean UI design and logic separation.

---

## **2. How JCB Integrates Templates into Site Views**

[00:03:31](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h03m31s)

Inside the compiled component, open `default.php` to confirm template inclusion.
You'll notice the same PHP-to-HTML transitions reflected in the generated code.

[00:04:22](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h04m22s)

Templates have access to all **global fields and class methods** available in the default view.
For instance, both can access:

```php
$this->preacher;
$this->params;
```

[00:05:07](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h05m07s)

When you place a snippet like `$this->loadTemplate('preacherpanel');` into the Site View code, JCB automatically links it to the corresponding template file under `tmpl/`.
That's how **templates become part of the Site View** during compilation.

---

## **3. Working With Layouts**

### **Quick Layout Example**

[00:05:52](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h05m52s)

Layouts are used differently from templates. While templates structure a single view's display, **layouts** are reusable display parts that can be shared across multiple templates or views.

[00:06:53](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h06m53s)

In Joomla conventions:

* **Templates** can include other **templates**,
* **Layouts** can include other **layouts**,
* But templates cannot include layouts directly.

[00:07:44](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h07m44s)

These rules stem from how Joomla implements rendering, not limitations in JCB.

---

### **Passing Data into Layouts**

[00:08:02](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h08m02s)

Layouts do not automatically have access to the same `$this` scope as templates.
You must **pass variables manually** when rendering them:

```php
echo JLayoutHelper::render('my_layout', ['items' => $this->items]);
```

This allows precise control over what data each layout receives.

[00:08:53](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h08m53s)

Within JCB, when creating a layout, you can choose which **Dynamic Get dataset** is available. However, the layout itself won't affect the Site View's data model-it's purely for display.

---

### **Adding Layouts to the Component**

[00:09:51](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h09m51s)

When you include a layout snippet (for example, in the default Site View), JCB ensures the corresponding layout file is created in your component's `/layouts/` directory.
This allows that layout to be reused in other templates and views as needed.

[00:10:19](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h10m19s)

> **Tip:** Layouts and templates function identically in **Custom Admin Views** within JCB.
> Both rely on snippets to include and render content modularly.

---

## **4. Summary of Template and Layout Integration**

[00:11:10](https://www.youtube.com/watch?v=6VBbi3Rl2eY&t=00h11m10s)

By combining templates and layouts effectively:

* You keep code modular and maintainable.
* You can reuse common structures across multiple views.
* Component Builder automates their linking via snippets during compilation.

**Templates** form the visual skeleton of each view.
**Layouts** let you organize smaller code blocks for repeated use across your component.

---

### **Key Takeaways**

* Templates reside in the `tmpl/` folder of each view and are added using `$this->loadTemplate('name');`.
* Layouts are shared code pieces stored in `/layouts/`, added using `JLayoutHelper::render()`.
* Templates have access to `$this` and all global view properties.
* Layouts require explicit variable passing.
* Joomla's conventions govern how templates and layouts can be nested.
