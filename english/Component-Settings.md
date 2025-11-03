# Component Settings in Joomla Component Builder

Joomla Component Builder (JCB) lets you describe almost every part of an extension without leaving the web interface. The **Component Settings** area is where you stitch custom menus together, import bespoke files, and expose configuration options to administrators and menu items. This guide turns the original transcript into a reference you can scan and apply while building real projects.

## Prerequisites

Before working in Component Settings make sure you have:

- A component created in JCB with at least one administrator view.
- Any custom code or layouts prepared in the `/custom` folder of your JCB installation if you plan to import files.
- The field names you want to expose globally already created under **Fields**.

> Need a refresher on what a component controls? Read [Joomla Components in JCB](./Joomla-Components.md) for the full list of assets that compile together.

## Navigating the Component Settings workspace

Component Settings consists of three high-impact tabs:

1. **Admin Views & Site Views:** connect the views you created elsewhere in JCB.
2. **Custom Admin Menus:** create extra administrator menu entries that point to custom controllers or external links.
3. **Config:** expose component-wide parameters (and, when convention is followed, their menu overrides).

Each tab works together. Custom menus generally load code you imported via the **Files** tab, and config fields must already exist under **Fields** before you can assign them here.

## Building custom administrator menus

Use **Custom Admin Menus** when you want an extra navigation item that is not generated from a standard view.

1. **Define the menu item** – provide a title, internal code name, optional external link, and pick an icon.
2. **Choose placement** – decide whether the menu appears in the main component navigation or as a submenu and choose where it sits relative to existing entries.
3. **Link supporting code** – if the menu should open a bespoke view, ensure that the controller, model, and layout files are imported via the **Files** tab (see below).

This is how the JCB compiler view itself is bundled: its controller, model, view, and helper files are kept in a `compiler` folder under `/custom`, then mapped into `admin/views/compiler` at build time. The custom menu simply points to that view.

## Importing custom files and folders

Sometimes you need files that JCB does not generate automatically (for example, PHPExcel, a bespoke controller, or a layout). Use the **Files** tab in the component to import them.

1. Place your assets inside the `custom` directory of your JCB installation, mirroring the destination structure you expect (folders are allowed).
2. In Component Settings → **Files**, map each asset or folder to its target location. You can rename the destination file as part of the mapping.
3. When the component compiles, JCB first creates the destination folders and then moves your custom assets into place.

Using folders keeps related files together. For example, dropping an entire `compiler` folder ensures all of its files arrive under `admin/views/compiler` without listing them one by one.

## Configuring global component options

The **Config** tab drives the Joomla Options screen that appears when you open your component and click **Options**. These settings can manage timers, versioning, contributors, permissions, and any custom toggles you create.

### Create the underlying fields first

1. Go to **Fields** and create the field definitions you need (radio buttons, dropdowns, spacers, etc.).
2. Give each field a unique **System Name** such as `preachers_display` or `categories_display`. Reusing names causes conflicts when options are saved.

### Add fields to the Config tab

- For each setting, select the previously created field and assign it to a **Tab Name**. Fields with the same tab name are grouped in Joomla's Options modal in the order shown here.
- You can include spacer fields to improve readability. JCB recognises repeated spacer names and reuses them safely.
- Provide default values when you want newly installed components to ship with recommended settings. These defaults are written to the database during installation.

### Automate frontend menu overrides

JCB automatically mirrors configuration tabs into frontend menu parameters when you follow a simple convention:

1. Match the Config tab name to the name of the frontend view (for example, a tab called `Preachers` maps to the `preachers` list view).
2. Ensure the frontend view is configured to generate menu parameters (`Add as Menu` set to **Yes**). JCB then creates a `default.xml` layout alongside the view with the same fields.
3. Within your view's PHP (`view.html.php` or layout files) fetch the parameters using `$params = $this->state->get('params');` or `$app->getParams();` and honour the user's choices. Joomla automatically falls back to the global value when the menu item is set to **Use Global**.

This is how the Seven Distributor demo component exposes choices such as “table”, “grid”, or “list” across both the Options screen and each menu item.

## Advanced tools: MySQL tweak

The **MySQL Tweak** area is intended for complex distribution scenarios where you ship multiple editions of the same component. It allows you to include or exclude demo data per release. Most builders can ignore it until they curate separate packages.

## Recommended conventions

- Adopt consistent prefixes (such as `preachers_`, `categories_`) for related Config fields to avoid naming collisions.
- Keep supporting documentation inside your repository so future maintainers know why a field exists.
- Test each custom menu item after compilation to confirm that included files are copied to the expected location.

## Related resources

- [Component Settings Overview](./Component-Settings-Overview.md) – screenshot-driven orientation for the same interface.
- [Manage a Component's Global Config Option Field in Relation With Menu Params](./Manage-a-Components-Global-Config-Option-Field-in-Relation-With-Menu-Params.md) – deeper look at how menu overrides interact with component options.
- [Automatic Import of Custom Code During Compilation](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) – strategies for managing reusable code packages.
