# Forking JCB Snippets to Share with the Community

[Watch Full Tutorial on YouTube](https://www.youtube.com/watch?v=0hgHeQVTLOk&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

This guide explains how to **fork**, **clone**, and **contribute** JCB community snippets through GitHub, using the **Snippet Manager**.
By following these steps, you'll be ready to make a pull request and contribute your own or improved snippets to the Joomla Component Builder (JCB) community.

---

## Overview

[00:00:00](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h00m00s)

Once familiar with the new Snippet Manager, the next step is to learn how to **take shared snippets** and **share your own** with the community.

This process involves:

1. Forking the official JCB Snippets repository.
2. Exporting snippets from JCB that you want to contribute.
3. Committing your changes and submitting a pull request.

---

## Step 1. Fork the JCB Snippets Repository

[00:00:18](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h00m18s)

You'll need:

* A **GitHub account**.
* Basic understanding of **Git**.

The official JCB Snippets repository is hosted at:

👉 [https://github.com/vdm-io/Joomla-Component-Builder-Snippets](https://github.com/vdm-io/Joomla-Component-Builder-Snippets)

### Forking the Repository

[00:05:06](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h05m06s)

1. Open the repository in your browser.
2. Click **Fork** (top right).
3. Choose your personal account or organization as the fork destination.
4. GitHub will copy the repository into your account.

---

## Step 2. Set Up Your Local Development Environment

### Clone the Repository

[00:06:50](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h06m50s)

Use the `Clone` button to copy the repository to your local machine.

```bash
git clone git@github.com:YourUserName/Joomla-Component-Builder-Snippets.git
cd Joomla-Component-Builder-Snippets
```

> **Tip:** Use SSH for security if you're familiar with SSH keys; otherwise, use HTTPS.

After cloning, you'll see all files locally. Avoid editing them directly - instead, make all snippet modifications within **Joomla Component Builder** and export them properly.

---

## Step 3. Export Snippets from JCB

[00:10:59](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h10m59s)

You can:

1. **Add new snippets.**
2. **Improve existing snippets.**
3. **Move snippets to a different type.**

### Naming Convention (Critical)

Each exported snippet's file name follows a strict convention:

```
Library Name - (Type) Snippet Name.json
```

Example:

```
Uikit v2 - (Common) Animation slide-top reverse.json
```

**Never alter these three components**:

* **Library**
* **Type**
* **Snippet Name**

Changing any will create a **new snippet** and possibly cause duplicates.

> **Tip:** Before submitting, confirm the snippet's type and naming convention match community standards.

---

## Step 4. Add, Improve, or Move Snippets

### Moving a Snippet

[00:11:27](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h11m27s)
Example: moving `FooTable` from **Layout** to **Tables**.

### Adding a New Snippet

[00:14:06](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h14m06s)
Example: creating a new **Accordion** snippet under `Uikit v3 → Collapse`.

### Improving an Existing Snippet

[00:16:20](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h16m20s)
Example: adding usage notes to the `Uikit v2 Form` snippet.

When creating or editing snippets, your **GitHub contributor details** will automatically be linked for recognition within the community.

---

## Step 5. Export and Prepare for Commit

[00:18:12](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h18m12s)

After exporting:

1. Locate the exported ZIP file in your JCB `/tmp/snippets` directory.
2. Unzip it.
3. Move (cut and paste) the JSON files into your local cloned repository folder.
4. Replace improved files when prompted.

> **Important:** Use `git rm` to remove outdated snippets so that removal is properly recorded with a commit message.

---

## Step 6. Commit Your Changes

### Check Git Status

```bash
git status
```

### Remove Old Snippets

[00:21:10](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h21m10s)

```bash
git rm "FooTable - (Layout) FooTable.json"
git commit -m "Removed FooTable - (Layout) FooTable.json since it was moved to Tables type."
```

### Add Updated or New Snippets

[00:23:03](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h23m03s)

```bash
git add "FooTable - (Tables) FooTable.json"
git commit -m "Updated FooTable snippet to correct Tables type."
```

For new snippets:

```bash
git add "Uikit v3 - (Collapse) Accordion.json"
git commit -m "Added Accordion snippet for Uikit v3."
```

> **Tip:** Commit frequently and descriptively-each major change should have its own message.

---

## Step 7. Keep Your Fork Synced with the Upstream Repository

### Add the Upstream Remote

[00:28:03](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h28m03s)

```bash
git remote add upstream https://github.com/vdm-io/Joomla-Component-Builder-Snippets.git
git remote -v
```

### Sync Your Fork

[00:31:01](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h31m01s)

```bash
git fetch upstream
git checkout master
git merge upstream/master
```

> Always perform these steps **before** pushing and creating a pull request to ensure your fork is up to date.

---

## Step 8. Push Your Changes to GitHub

[00:34:00](https://www.youtube.com/watch?v=0hgHeQVTLOk&t=00h34m00s)

```bash
git push origin master
```

This uploads all commits, additions, and deletions to your forked repository on GitHub.

After refreshing your GitHub page, it should display:

> "This branch is X commits ahead of vdm-io:master."

You are now ready to create a **pull request** (covered in the next tutorial).

---

## Best Practices & Recommendations

* Always export snippets through **JCB**, not by manual editing.
* Follow the **file naming convention** strictly.
* Write **clear and descriptive commit messages**.
* Use **separate commits** for new, improved, and moved snippets.
* Keep your fork regularly **synced** with upstream before submitting pull requests.

---

### Helpful Links

* **Official JCB Snippets Repository:**
  [https://github.com/vdm-io/Joomla-Component-Builder-Snippets](https://github.com/vdm-io/Joomla-Component-Builder-Snippets)
* **Git Quick Start (Udemy):**
  [https://www.udemy.com/git-quick-start/](https://www.udemy.com/git-quick-start/)
* **Uikit Accordion Docs:**
  [https://getuikit.com/docs/accordion](https://getuikit.com/docs/accordion)

---
