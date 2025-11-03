# Forking JCB Snippets to Share with the Community

[Watch Full Tutorial on YouTube](https://www.youtube.com/watch?v=0hgHeQVTLOk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

This guide explains how to **fork**, **configure**, and **contribute** JCB community snippets through GitHub using the refreshed
**Snippet Manager** workflow. The snippets area now uses the same **Reset → Init → Push** tooling that powers JCPackages, so you
can pull updates, work locally, and contribute changes without leaving the JCB interface.

---

## Overview

Once familiar with the Snippet Manager you can:

1. Fork the global snippets repository so you have your own remote.
2. Use **Reset** and **Init** to prepare and pull snippets directly into JCB.
3. Improve or create snippets inside the application.
4. Use **Push** to send your work back to GitHub and open a pull request.

The community repository lives at [github.com/joomengine/snippets](https://github.com/joomengine/snippets). Everyone can pull
from this remote, and contributions are shared with the wider community through pull requests.

---

## Step 1. Fork the JCB Snippets Repository

You'll need a **GitHub account** and a basic understanding of Git.

1. Visit [github.com/joomengine/snippets](https://github.com/joomengine/snippets).
2. Click **Fork** (top right).
3. Choose your personal account or organization as the fork destination.
4. GitHub will copy the repository into your account. The URL of your fork will look like
   `https://github.com/<your-user>/snippets`.

You now have a writable repository that you can push to from JCB.

---

## Step 2. Configure Your Fork Inside JCB

The Snippet Manager keeps a list of repositories just like the JCPackages area.

1. Open **Components → Joomla Component Builder → Snippets**.
2. Click **Reset** on the toolbar to open the repository configuration dialog.
3. Add a new repository (or edit an existing entry) with:
   * **Name** – Any label that helps you identify the remote (e.g. “My Fork”).
   * **Remote URL** – The HTTPS or SSH URL of your fork (`https://github.com/<your-user>/snippets.git`).
   * **Branch** – Usually `main` unless you created a different default branch.
4. Confirm the dialog. JCB prepares a local working copy of that repository on your filesystem.

After Reset completes you can switch between remotes at any time by opening the repository selector and choosing the entry you
added.

---

## Step 3. Initialize Snippets from a Repository

1. With your repository selected, click **Init**.
2. Choose the remote you want to load from (community upstream or your fork).
3. JCB retrieves the latest metadata and lists every available snippet grouped by library and type.
4. Tick the snippets you wish to pull in and confirm.

JCB clones or updates the underlying Git repository automatically and adds the selected snippets to your local catalogue. You can
repeat **Init** whenever you want to fetch additional snippets or refresh the local copy of a snippet.

---

## Step 4. Add or Improve Snippets in JCB

Work directly inside the Snippet Manager:

* Create new snippets with clear descriptions, usage notes, and accurate library/type assignments.
* Update existing snippets while keeping the **Library**, **Type**, and **Name** consistent so JCB tracks them as updates instead
  of new entries.
* Make sure your contributor details are set under **Global Options → Company Tab** so JCB tags your changes correctly.

Every change is written to the local Git working copy, allowing you to review differences before pushing.

---

## Step 5. Push Changes Back to GitHub

1. Select the snippets you want to publish.
2. Click **Push**.
3. Provide a short, descriptive commit message summarizing your work if prompted.
4. JCB stages the selected snippets, commits them to the local repository, and pushes the commit to the remote you configured.

If you are using a personal fork, the push updates your repository instantly. Team members or automation can pull those changes
from the same remote.

---

## Step 6. Open a Pull Request

To share your improvements with the global community:

1. Visit your fork on GitHub after pushing. You will see a banner inviting you to **Compare & pull request**.
2. Review the diff to ensure it contains only the intended snippet changes.
3. Describe why the update is valuable and reference any related issues or discussions.
4. Submit the pull request back to `joomengine/snippets`.

Project maintainers will review your contribution, offer feedback if needed, and merge it so everyone can benefit.

---

## Best Practices & Recommendations

* Always make edits through JCB so metadata stays correct.
* Keep the **Library**, **Type**, and **Snippet Name** fields stable unless you are intentionally moving a snippet.
* Use clear commit messages whenever you push.
* Pull from the upstream repository regularly (via **Init**) to stay aligned with community updates.
* If you manage internal snippets, add a separate repository entry so you can switch between private and community catalogues.

By following this workflow you can confidently collaborate on snippets, reuse community contributions, and keep your own projects
in sync with the global catalogue.
