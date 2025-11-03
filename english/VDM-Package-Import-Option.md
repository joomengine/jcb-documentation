# Repository Index & Demo Packages

JCB no longer downloads ZIP archives from the “VDM Packages” tab. Instead, you can initialise a
repository index that lists official demo components and helper libraries. This page explains how to
bring the catalogue into your installation, explore the included documentation, and import the
blueprints you need.

---

## 1. Load the Repository Index

1. Go to **Components → Component Builder → Repositories**.
2. Click **New** and create an entry for the index:
   * **Organization:** `joomengine`
   * **Repository:** `repoindex`
   * **Read Branch:** `master`
   * **Type:** `GitHub`
   * **Target Content:** `repositories`
   * **Access:** `global`
3. Save the record and return to the list view.
4. Press **Init**, select the repo index entry, and choose **Initialize Selected Repositories**.

JCB clones the index, creates local records for every listed repository, and displays their README
files directly in the interface. You now have instant access to the demo catalogue.

---

## 2. Explore the Included Demo Components

After initialisation you will see repositories for:

* **Joomla 4 Demo Component**
* **Joomla 5 Demo Component**
* **Hello World for Joomla 5**
* **Recipe Manager for Joomla 5**
* **E-Health Portal for Joomla 5**

Each entry includes documentation that highlights the patterns used in the component, such as
multi-view relationships, custom field types, or advanced routing examples.

---

## 3. Import a Demo Using Init

1. Open the entity type that matches the repository (e.g. **Components** for the demo component).
2. Select **Init** in the toolbar.
3. Pick the repository entry you want to import and confirm.
4. Review the README to understand prerequisites or optional dependencies.

JCB imports the blueprint, resolves any linked field types, snippets, or superpowers, and makes the
component available in your installation. Compile it as usual to generate a Joomla extension ZIP for
local testing.

---

## 4. Reset to Pull Updates

When the upstream repository receives improvements:

1. Ensure only the repositories you trust are **published** for the relevant target content.
2. Open the entity and press **Reset**.
3. JCB pulls the latest commit and updates the blueprint, keeping your local copy in sync.

If multiple repositories provide the same entity, drag them into the desired order or temporarily
unpublish alternatives before resetting.

---

## 5. Use the README as Documentation

The packaging engine doubles as a documentation viewer. Each repository README may include:

* Overview of the component or library
* Setup and configuration notes
* Links to tutorials, issues, or sample data
* Contribution guidelines

Read the documentation before importing so you understand how the blueprint fits into your project.

---

## 6. Next Steps

* Import additional repositories from the catalogue (field types, snippets, powers) as needed.
* Fork the repositories to customise demos or propose improvements.
* Contribute new blueprints by following the
  [package publishing workflow](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md).

The repository index keeps your JCB installation stocked with maintained demo projects that reflect
the latest best practices.
