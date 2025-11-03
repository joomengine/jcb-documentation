# Proposed Collaborative Workflow in Joomla Component Builder (JCB)

JCB’s packaging engine turns every blueprint into a Git repository. That means teams can collaborate
on components, field types, snippets, and powers with the same Git-based discipline used for source
code. This guide outlines a practical workflow that combines JCB’s UI with Git branches, pull
requests, and repository documentation.

---

## 1. Understand JCB’s Built-in Safeguards

JCB keeps collaborative work predictable even before Git enters the picture:

* **Check-in/check-out** – when a user edits a component, JCB locks it until they save and close the
  form. This prevents conflicting edits on the same Joomla site.
* **Permissions** – Joomla’s ACL controls who can view, edit, or manage specific entity types inside
  JCB. Configure permissions under *Components → Component Builder → Options → Permissions* to match
  your team roles.

These guardrails are still important when each developer runs a local Joomla instance – they ensure
consistency if multiple people connect to the same site for quick fixes or demos.

---

## 2. Prefer Local Development, Sync Through Git

Most teams run JCB on local containers, VMs, or dedicated development servers. Local work keeps your
Joomla environment fast, disposable, and isolated. To collaborate, developers exchange the JCB
blueprints through the packaging engine instead of sharing database dumps or ZIP exports.

> 🧠 **Tip:** Automate local setup (e.g. Docker + OctoJoom) so every developer can recreate the same
> environment before importing repositories.

---

## 3. Bootstrap Repositories with the Catalogue

1. Register the `joomengine/repoindex` repository in JCB (see the
   [JCB Packaging Engine guide](./JCB-Packaging-Engine.md)).
2. Use **Init** in the Repositories list to clone the catalogue and create entries for official demo
   packages, field type libraries, and helper repositories.
3. For each entity you plan to collaborate on, open it and press **Init** to link the relevant
   repositories.

Every repository entry includes documentation that explains how the blueprint works, expected
dependencies, and contribution notes.

---

## 4. Learn the Init → Reset → Push Cycle

Once a repository is linked to an entity:

* **Init** – imports the blueprint for the first time. Run this when onboarding a new developer or
  when you need to add a blueprint from the catalogue.
* **Reset** – pulls the latest commit from the published repositories. Use it after a teammate merges
  a pull request so your local copy matches the canonical repository.
* **Push** – publishes your local changes back to Git. Make sure the repository entry has a write
  branch and valid credentials. Push affects every published repository for that target content, so
  unpublish any destinations you do not want to update.

Developers can now collaborate in parallel: each person works locally, pushes to their fork, and opens
pull requests for review.

---

## 5. Recommended Git Workflow

1. **Fork** the upstream repository (e.g. `joomengine/packages`).
2. **Clone** your fork locally and register it in JCB with both read and write branches.
3. **Init** the relevant entities so they point to your fork.
4. Make changes inside JCB, run **Push**, and commit the resulting files.
5. Open a **pull request** against the upstream repository describing the update and linking to any
   related issues or discussions.
6. Once merged, other developers **Reset** their local copies to receive the changes.

Because repositories are plain Git, you can branch, tag releases, run CI, and review diffs before
accepting changes.

---

## 6. Example: Sharing a Component Blueprint

Imagine a team maintaining a complex CRM component:

1. The tech lead forks `joomengine/packages`, creates `acme-crm`, and documents dependencies on custom
   field types.
2. Each developer registers the fork in their JCB installation, presses **Init**, and imports the
   component.
3. Developers work on separate features in JCB. When ready, they **Push** to their fork, commit, and
   open a pull request.
4. The reviewer tests the change by pulling the branch locally, running **Reset**, and compiling the
   component.
5. After the pull request is merged, everyone runs **Reset** to synchronise their local blueprints and
   continues development.

This mirrors conventional Git workflows while letting JCB handle dependency resolution and ID
remapping behind the scenes.

---

## 7. Optional: Remote Synchronisation

The **Servers** feature (SFTP integrations) can mirror repositories between remote JCB installations.
Use it when you need a central staging server to consolidate work from multiple teams. Even with SFTP
sync, keep the Git repositories as the source of truth – it provides history, review tools, and safer
rollbacks.

---

## 8. Keep Security in Mind

* Store GitHub tokens securely using JCB’s encrypted options.
* Limit repository write access to trusted users.
* Review pull requests carefully, especially when they add superpowers or snippets that execute PHP.
* Document deployment procedures in the repository README so new contributors follow the same steps.

---

## 9. Additional Resources

* [JCB Packaging Engine](./JCB-Packaging-Engine.md)
* [Publish Your JCB Packages](./Add-your-own-JCB-packages-to-the-JCB-Communty-Directory.md)
* [Import JCB Packages](./How-to-install-jcb-packages.md)
* [Automated Backup System](./Automated-backup-system-in-JCB.md)

Adopting the packaging engine keeps your JCB projects transparent, reviewable, and easy to share
across multiple Joomla instances.
