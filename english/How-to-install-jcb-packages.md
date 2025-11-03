# Import JCB Packages with the Repository Engine

The Joomla 4+ generation of Joomla Component Builder (JCB) replaces the legacy ZIP importer with a
Git-backed packaging engine. Instead of uploading encrypted archives, you connect JCB to a
repository, browse the packaged entities, and pull the blueprint you need. This guide walks through
setting up the catalogue, importing blueprints, and controlling which repositories are allowed to
update your installation.

> 🔄 **Reminder:** A JCB package is a blueprint that lives inside JCB. It is *not* the Joomla
> extension ZIP that you install on a site. Use the packaging engine when you want to share or reuse
> the database definitions of components, fields, snippets, powers, and other entities.

---

## 1. Prepare the Repository Catalogue

The packaging engine reads Git repositories that are registered in **Components → Component Builder →
Repositories**. To load the official catalogue:

1. Click **New** and create an entry with:
   * **Organization:** `joomengine`
   * **Repository:** `repoindex`
   * **Read Branch:** `master`
   * **Type:** `GitHub`
   * **Target Content:** `repositories`
   * **Access:** `global`
2. Save the repository and return to the list view.
3. Press **Init** on the toolbar, select the repo index entry, and choose
   **Initialize Selected Repositories**.

JCB clones the catalogue and creates local records for every referenced repository. Each repository
includes Markdown documentation that explains what the package provides.

---

## 2. Link the Repositories You Need

Each packagable entity (components, field types, snippets, superpowers, etc.) has an **Init** button.
Use it to link the entity to one or more repositories:

1. Navigate to the entity list (e.g. **Components**) and open an item.
2. Click **Init** in the toolbar.
3. Choose the repositories that match the entity’s target content.
4. Confirm to link them to your installation.

Once linked, the repository appears in the entity’s sidebar with metadata, readme content, and a list
of available blueprints.

---

## 3. Import Blueprints with Init & Reset

* **Init** imports a blueprint for the first time. Select the item you want from the repository list
  and confirm. JCB creates the entity locally and resolves any dependencies automatically
  (e.g. field types, snippets, or superpowers referenced by the package).
* **Reset** re-syncs the local entity with the repository. Use it to pull upstream changes after a
  collaborator pushes an update. JCB respects the repository order – move preferred sources to the
  top and unpublish repositories you want to ignore.

Because repositories are prioritised, you can keep multiple upstreams available. Publish only the
repositories you trust before running Reset to avoid accidental overrides.

---

## 4. Review the Repository Documentation

Every repository includes a Markdown readme that JCB renders next to the entity controls. Use it to:

* Understand the scope of the blueprint before importing it.
* Read upgrade or migration notes provided by the package author.
* Follow links back to GitHub issues, pull requests, or example sites.

Treat the readme as the authoritative documentation for that package. If something is unclear, open
a discussion or issue in the source repository.

---

## 5. Configure GitHub Tokens for Private Imports

Public repositories can be read anonymously, but pushing changes or importing from private
repositories requires authentication.

1. Generate a GitHub personal access token with the `repo` scope.
2. Add it globally under *Components → Component Builder → Options → GitHub* **or** edit a
   repository entry and enable **Override Global Settings** to store a per-repository token.
3. For self-hosted Git servers, provide the matching credentials in the repository settings.

Tokens are stored encrypted inside Joomla. Rotate them periodically according to your organisation’s
security policies.

---

## 6. Troubleshooting Imports

| Symptom | What to check |
| --- | --- |
| Repository list is empty | Confirm that the repo index was initialised and the repository entry is **published**. |
| Reset pulls the wrong version | Reorder repositories for the target content or temporarily unpublish the ones you do not want. |
| Push is disabled | The repository entry needs a **write branch** and valid credentials. Remember that pushes affect **all** published repositories for that target content. |
| Missing dependencies | Import related repositories (e.g. field types or snippets) and ensure they are published before running Reset. |

---

## 7. Next Steps

* Explore the [JCB Packaging Engine overview](./JCB-Packaging-Engine.md) for a deep dive into
  target content channels and collaborative workflows.
* Read the repository-specific docs to learn how each blueprint should be used.
* When you are ready to share your own work, follow the
  [package publishing guide](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md) to
  connect your repositories and push updates back to Git.

By relying on repositories instead of ad-hoc ZIP files, teams can keep every JCB blueprint
synchronised, reviewable, and version controlled.
