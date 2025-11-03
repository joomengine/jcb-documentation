# JCB Packaging Engine

<a id="why-the-packaging-engine-matters"></a>
## 📦 Why the Packaging Engine Matters

Joomla Component Builder (JCB) now ships with a **Git-driven packaging engine** that replaces the
legacy ZIP package workflow used during the Joomla 3 era. Instead of exporting encrypted archives
and passing them around manually, you can link any JCB entity to a Git repository, read its
documentation, synchronise the blueprint, and collaborate through standard pull requests.

Think of the packaging engine as the **blueprint exchange** for JCB:

* A **Joomla component package** (the ZIP you install into Joomla) contains the compiled PHP, XML,
  and assets that power a site.
* A **JCB package** stores the *definition* of that component – the admin views, fields, field
  types, snippets, templates, superpowers, and other metadata that lives inside the JCB database.

By publishing those definitions to Git repositories, teams can fork, branch, review, and merge
changes exactly like any other code base.

---

<a id="what-can-be-packaged"></a>
## 🧱 What Can Be Packaged

Every major entity inside JCB can be exported, versioned, and synchronised via the packaging engine:

* Fields and Field Types
* Admin Views, Site Views, and Custom Admin Views
* Components and their settings
* Snippets, Layouts, and Templates
* Superpowers and Joomla Powers
* Any other entity that appears in the packaging interface

To make the system predictable, JCB groups entities into **target content channels**. Each channel
maps to one or more repositories:

1. **Superpowers** – PHP classes that live entirely within JCB
2. **Joomla Powers** – references to Joomla core services
3. **Field Types** – templates and logic for reusable form inputs
4. **Snippets** – HTML/CSS/JS building blocks
5. **Packages** – full components, views, layouts, and other blueprints
6. **Repositories** – metadata used to bootstrap the entire network

JCB will read and write to every repository that shares the same target content and is published.

---

<a id="repository-index"></a>
## 🗂 Repository Index & Documentation Engine

The packaging engine doubles as a documentation browser. Each repository contains a `package.json`
file plus Markdown readme content that JCB renders directly in the interface. When you browse or
initialise a repository, you are not only importing the data – you are also seeing the repository’s
own documentation about how that blueprint works.

To load the official catalogue:

1. Open **Components → Component Builder → Repositories**.
2. Click **New** and enter:
   * **Organization:** `joomengine`
   * **Repository:** `repoindex`
   * **Read Branch:** `master`
   * **Type:** `GitHub`
   * **Target Content:** `repositories`
   * **Access:** `global`
   * **Name:** any descriptive label (e.g. *JoomEngine Repo Index*)
3. Save the repository entry and click **Init** from the Repositories list.
4. Select the new entry and choose **Initialize Selected Repositories**.

JCB clones the repo index, reads its catalogue, and creates local records for every referenced
repository. Their readme files appear directly in the UI so that you always import blueprints with
context.

---

<a id="init-reset-push"></a>
## 🚀 Button Flow: Init → Reset → Push

Once repositories exist, every packagable entity exposes three actions:

### 🔹 Init
Links the current entity to a repository and lists remote blueprints that can be imported. Use it
when you want to bring an entity into your installation for the first time.

### 🔹 Reset
Refreshes the local entity from the latest version in the repository. JCB honours repository order
for the same target content – publish the sources you trust and unpublish or archive the rest. When
you only want to read from one repository, temporarily unpublish the others before pressing Reset.

### 🔹 Push
Sends your local changes back to the repository. Requirements:

* The repository entry must define a **write branch** and be published.
* Your Joomla site must have a valid **GitHub token** – either globally in
  *Options → GitHub Settings* or per repository via **Override Global Settings**.
* Your user account needs write access to the destination repository.

Push runs for **every published repository** assigned to the same target content. Remove the write
branch or unpublish unused repositories when you want to limit the push destination.

---

<a id="git-authentication"></a>
## 🔐 Git Authentication

You can store a personal access token in two places:

* **Global token** – set it once under *Components → Component Builder → Options → GitHub*.
* **Repository override** – edit a repository entry, enable *Override Global Settings*, and add a
token that should only be used for that repository.

Tokens are stored encrypted inside JCB. Make sure they allow the `repo` scope so pushes succeed.

---

<a id="dependency-resolution"></a>
## 🔄 Dependency Resolution & Ordering

Importing or resetting a blueprint pulls in every linked entity automatically. If an admin view
uses a field type or a component depends on snippets, those references are resolved from the active
repositories. When multiple repositories provide the same entity, JCB honours the list order within
that target content:

1. Publish only the repositories you trust.
2. Drag them into the preferred priority order.
3. Use **Reset** to rehydrate your local entities.

This makes it possible to stage experimental repositories, keep a canonical upstream, and only
switch sources when you deliberately change the order.

---

<a id="example-workflow"></a>
## 🧰 Example Workflow

1. **Create a repository** for your component blueprints (e.g. `your-org/component-blueprints`).
2. In JCB, add a repository entry with the correct target content (`packages` for full components,
   `field_types` for field libraries, etc.) and define read/write branches.
3. Design your component as usual inside JCB.
4. Click **Push** on the component to publish the blueprint to Git.
5. Team members add the same repository entry, press **Init**, and select the component to import.
6. Everyone edits in their own JCB instance, pushes changes, and collaborates through pull requests
   exactly like any other Git project.

Because repositories include Markdown documentation, your blueprint can ship with usage guides,
configuration notes, sample data, or upgrade instructions.

---

<a id="fork-and-pr"></a>
## 🤝 Forks, Pull Requests & Community Repos

The official JoomEngine catalogue lives at [github.com/joomengine](https://github.com/joomengine).
To contribute:

1. **Fork** the repository that matches the target content (for example `joomengine/packages`).
2. Add your fork inside JCB so it appears alongside the official upstream.
3. Develop locally, press **Push**, and commit from your Git client.
4. Open a pull request describing what changed. Linking to issues or discussions is encouraged.

Because blueprints live in Git, you can review diffs, tag releases, and automate testing just like
any software project.

---

<a id="best-practices"></a>
## ✅ Best Practices

* **Segment repositories** by purpose: keep field types separate from component blueprints to avoid
  unnecessary dependencies.
* **Name repositories clearly** and match the JCB system name to the Git slug for easy discovery.
* **Document everything** in the repository readme – JCB surfaces it directly in the interface.
* **Always Init before Push** when working on a new machine so your local entities are linked to the
  correct repository history.
* **Unpublish unused repositories** to prevent accidental pushes or resets.
* **Treat the repository as the source of truth** – the Joomla database is just your working copy.

---

<a id="further-reading"></a>
## 📚 Further Reading

* Official repository index: [https://github.com/joomengine/repoindex](https://github.com/joomengine/repoindex)
* Packaging discussion thread: [JoomEngine Discussions #995](https://github.com/orgs/joomengine/discussions/995)
* Collaborative workflow guide: [Proposed Collaborative Workflow in JCB](./Proposed-Collaborative-Workflow-in-JCB.md)
* Publishing tutorials: [Add Your Own JCB Packages to the Directory](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md)

Use these resources to design repeatable workflows where every change to your JCB blueprints is
reviewed, versioned, and shareable.
