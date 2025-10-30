# Making a Pull Request at Joomla Component Builder Snippets

This guide explains how to **submit your snippet contributions** to the official Joomla Component Builder (JCB) Snippets repository by creating a **pull request** (PR). It follows the exact workflow demonstrated in the [video tutorial](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s) and provides a clear, beginner-friendly explanation of each step.

---

## 1. Overview of the Pull Request Process

[00:00:00](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h00m00s)

A pull request (PR) allows you to submit your **committed changes** from your **forked version** of the `vdm-io/Joomla-Component-Builder-Snippets` repository back to the official repository.

* You'll be contributing to the **Snippets library** used by the JCB community.
* The JCB team and other community managers will review and merge valid contributions.
* Always work on your **own forked repository** rather than the master branch.

---

## 2. Preparing Your Fork for Contribution

[00:01:05](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m05s)

Before you create a PR, make sure you have:

1. **Forked** the main repository (`vdm-io/Joomla-Component-Builder-Snippets`).
2. **Cloned** your fork locally.
3. **Unzipped and updated** the snippet files into your local repository.
4. **Committed** all your changes with clear commit messages.
5. **Synchronized your branch** with the upstream (master) branch to avoid conflicts.

> 💡 **Tip:** If you're unsure about forking or syncing your repository, watch the **previous tutorial** in the playlist before proceeding.

---

## 3. Checking Your Commit Status

[00:01:43](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h01m43s)

Once your commits are ready and pushed to GitHub:

* Go to your forked repository.
* You'll see a message like:

  ```
  This branch is 4 commits ahead of vdm-io:master.
  ```
* Click **"Pull request"** to start the PR process.

---

## 4. Confirming Repository and Merge Status

[00:02:08](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h02m08s)

GitHub will show:

* **Base repository:** `vdm-io/Joomla-Component-Builder-Snippets (master)`
* **Head repository:** your fork and branch

If GitHub shows **"Able to merge"**, everything is ready.

You can also review:

* Each **commit message**
* Each **file change**
* Examples include snippet name changes like:

  ```
  FooTable - (Layout) FooTable.json → FooTable - (Table) FooTable.json
  ```

> ✅ **Good practice:** Write clear and concise commit messages to make review easier and faster.

---

## 5. Submitting Smaller Contributions

[00:04:08](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m08s)

Start small. Submit a few snippets at a time, especially if this is your first contribution.

* Avoid submitting **large bulk changes** unless you're a trusted contributor.
* Smaller PRs are easier to review and merge quickly.

---

## 6. Creating the Pull Request

[00:04:41](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h04m41s)

1. Click **"Create pull request"**.
2. Provide a **title** and **description** summarizing the contribution.

### Example:

**Title:**

> "Added Accordion Snippet and Updated FooTable Layouts"

**Description:**

> * Added new Accordion snippet
> * Updated FooTable snippet layout to table type
> * Improved usage description field

> 🧭 In future, JCB may include predefined naming conventions and templates for pull request titles.

---

## 7. Admin Review Process

[00:05:43](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h05m43s)

Only administrators can manage the following fields:

* **Reviewers**
* **Assignees**
* **Labels**
* **Projects**
* **Milestones**

You don't need to fill these out - the JCB maintainers will handle it.

---

## 8. Writing the Pull Request Description

[00:06:27](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h06m27s)

Use your **commit messages** as a foundation for your pull request description.

1. Review your pull request summary before submission.
2. Click **"Create pull request"** once everything looks good.

After submission:

* Wait for admins to review.
* They may ask questions or request clarifications before merging.

> 🧠 **Note:** The review process ensures quality control and consistent naming and documentation across all community snippets.

Once approved by at least **two reviewers**, your pull request can be merged.

---

## 9. Merging into the Master Branch

[00:08:19](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h08m19s)

Admins have several merge options:

* Click **"Merge pull request"** directly on GitHub.
* If there are conflicts, advanced admins may resolve them using **command line tools**.

For conflicts, follow GitHub's **"command-line instructions"** link to learn how to merge manually.

---

## 10. Post-Merge: Visibility in JCB

[00:09:12](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m12s)

Once merged:

* The new or updated snippets become visible in **JCB's Snippet Get area**.
* Other users can now download and use them directly from JCB.

This streamlined integration keeps community snippets synced through GitHub without requiring manual database updates.

---

## 11. Managing Your Snippets

[00:09:52](https://www.youtube.com/watch?v=vQ-yxVtc-Co&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=00h09m52s)

Through your forked repository and JCB:

* You can **add**, **update**, **delete**, and **trash** snippets.
* Deleted snippets will no longer appear in your JCB Snippets area.

Example:

* Go to **Snippets → Accordion → Trash**
* Then **permanently delete** it from the *Trashed* section.

This will mark it as **non-existent** in your snippet repository.

> ✨ **Goal:** To make snippet sharing easy and collaborative without complex database updates.

---

## 12. Community Collaboration

When you contribute snippets:

* Your **name** is associated with the change in Git history.
* This allows you to **gain recognition** within the JCB community.

> 🏗️ "Share your snippets, help others, and make Joomla Component Builder stronger!"

---
