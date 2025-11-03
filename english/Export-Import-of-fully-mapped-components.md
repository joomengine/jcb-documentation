# Export & Import Fully Mapped Components via the Packaging Engine

The Git-based packaging engine introduced with Joomla 4 transforms how JCB shares complete component
blueprints. Instead of downloading encrypted ZIP archives, you push your components to a repository
and let other installations pull them through **Init** and **Reset**. This page explains how the
engine serialises every related entity, how to publish those exports, and how to import them on a
fresh site.

---

## 1. What the Packaging Engine Captures

When you push a component, JCB collects everything required to recreate it elsewhere:

* Components and settings
* Admin views, site views, and custom admin views
* Fields, field types, validation rules, and dynamic get relationships
* Layouts, templates, snippets, and language strings
* Superpowers, Joomla powers, and any dependency referenced by the component

The result is a **fully mapped blueprint** that mirrors the structure stored in your Joomla database.

---

## 2. Prepare a Repository

1. Register a repository under **Components → Component Builder → Repositories**.
2. Set **Target Content** to `packages` for full components and define read/write branches.
3. Provide authentication (GitHub token or other credentials) if the repository requires it.
4. Press **Init** so JCB links the repository and displays its README.

For team projects, fork the official catalogue repository first, then add your fork to JCB with a
write branch.

---

## 3. Export by Pushing the Component

1. Open the component in JCB.
2. Confirm it is linked to the repository via the sidebar.
3. Click **Push**.
4. JCB serialises the component and every related entity to the repository branch.
5. Use your Git client to review the changes, commit with a descriptive message, and push to the
   remote origin.

Because the export is stored in Git, you gain full history, diffing, and pull request review.

---

## 4. Import on Another Installation

1. On the target site, register the same repository and press **Init**.
2. Navigate to **Components**, click **Init**, and select the component from the repository list.
3. JCB creates the component locally, resolves dependencies, and updates IDs automatically.
4. If the component already exists, use **Reset** to pull the latest changes instead of importing a
   duplicate.

You can repeat the process for related repositories (field types, snippets, superpowers) to ensure
all dependencies are available before compiling the component.

---

## 5. Manage Versions and Branches

* Use Git branches to stage experimental work before merging to the main packaging branch.
* Tag releases so other installations can target a specific version when importing.
* Document upgrade steps in the repository README – JCB renders it alongside the Init/Reset buttons.

---

## 6. Troubleshooting

| Issue | Resolution |
| --- | --- |
| Component does not appear in the Init list | Ensure the repository entry is **published**, the correct target content (`packages`) is selected, and the read branch contains the exported blueprint. |
| Dependencies missing after import | Publish repositories for field types, snippets, or superpowers referenced by the component, then run **Reset** again. |
| Push fails | Verify the repository has a write branch, credentials are configured, and you have write permissions. |
| Unexpected overwrites | Reorder or temporarily unpublish repositories that should not update the component before running **Reset**. |

---

## 7. Compile & Deploy

After importing, compile the component to generate the Joomla installable ZIP. The packaging engine
keeps your blueprint synchronised while the compiler produces the runtime artefact for your Joomla
site.

Version-controlled exports make it straightforward to maintain backups, collaborate across multiple
installations, and audit every change introduced to a component.
