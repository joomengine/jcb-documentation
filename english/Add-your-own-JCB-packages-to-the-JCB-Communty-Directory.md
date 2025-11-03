# Publish Your JCB Packages to the Community Catalogue

The modern JCB packaging engine treats every blueprint as a Git repository. Sharing your work now
means publishing the entities (components, field types, snippets, etc.) to a repository and opening a
pull request so the community catalogue can list it. This guide explains how to prepare your package,
document it, and submit it for inclusion.

> 💡 **Terminology refresher:** A *JCB package* is a blueprint stored in Git. A *Joomla package* is the
> compiled ZIP you install on a Joomla site. The instructions below focus on blueprints.

---

## 1. Decide What You’re Publishing

JCB groups repositories by **target content**. Before creating a repository, decide which entity you
want to share:

| Target content | Typical use |
| --- | --- |
| `packages` | Full component blueprints (views, fields, layouts, scripts) |
| `field_types` | Reusable field type libraries |
| `snippets` | HTML/CSS/JS snippets for layouts and forms |
| `super_powers` & `joomla_powers` | Helper classes and integrations |
| `repositories` | Meta catalogue entries (used by maintainers) |

Separate repositories keep dependencies manageable. If your component relies on custom field types,
publish the field types in their own repository and list them as dependencies in your readme.

---

## 2. Fork or Create a Repository

1. If you want to contribute to the official catalogue, **fork** the relevant JoomEngine repository
   (for example `joomengine/packages`).
2. For organisation-specific work, create a repository under your own account or company namespace.
3. Clone the repository locally and add a README that explains what the blueprint provides, how to
   initialise it, and any configuration steps.

JCB renders the README inside the interface, so write it for end users.

---

## 3. Register the Repository in JCB

1. Go to **Components → Component Builder → Repositories**.
2. Click **New** and fill in:
   * **Organization** and **Repository** (matching the Git remote).
   * **Type** (GitHub, Gitea, etc.).
   * **Target Content** matching the table above.
   * **Read Branch** (e.g. `main` or `master`).
   * **Write Branch** if you plan to push from this JCB instance.
   * **Access** (`global`, `protected`, or `private`).
3. Save and press **Init** to link the repository. JCB will display the README and available
   blueprints.

If the repository is private, add a GitHub token under **Override Global Settings** or configure the
site-wide token in JCB’s Options.

---

## 4. Prepare the Blueprint Locally

Design or update your entity inside JCB as usual. When you are ready to publish:

1. Ensure the entity is linked to the correct repository (use **Init** if necessary).
2. Click **Push**. JCB serialises the entity and commits it to the repository branch.
3. Review the changes locally (`git status`, `git diff`) and commit with a clear message.
4. Push the commit to your remote fork.

> 🔁 **Tip:** Always run **Reset** after collaborators merge changes so your local copy stays in sync
> with the repository history.

---

## 5. Document Dependencies and Usage

Because repositories double as documentation, include the following in your README:

* Overview of what the package contains and when to use it.
* Dependencies on other repositories (link to their catalogue entries).
* Setup steps, sample data, or configuration hints.
* Versioning or migration notes for new releases.

Well-documented packages are more likely to be accepted into the community catalogue.

---

## 6. Submit to the Community Directory

To list your package alongside the official demos:

1. Open a pull request against the upstream repository (e.g. `joomengine/packages`).
2. Describe what the blueprint provides, how it was tested, and any prerequisites.
3. If required, add your repository metadata to the [`repoindex`](https://github.com/joomengine/repoindex)
   so other users can discover it through the Init workflow.
4. Monitor feedback from maintainers and update your PR if requested.

Once merged, the catalogue will list your package automatically and other JCB installations will see
it after refreshing the repository index.

---

## 7. Maintain Your Package

* Keep the README and package metadata up to date with every release.
* Tag Git releases so users can pin to a known state when needed.
* Respond to issues or discussions raised by the community.
* Archive old repositories if they are no longer supported so users do not accidentally import stale
  blueprints.

Publishing through the packaging engine ensures every blueprint is version controlled, documented,
and ready for collaborative development.
