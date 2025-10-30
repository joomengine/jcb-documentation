# Add Your Own JCB Packages to the JCB Community Directory

## Overview

This tutorial explains how to **add your Joomla Component Builder (JCB) packages to the JCB Community Directory**, allowing you to share your work, help others get started quickly, and reuse packages efficiently. It also introduces key JCB features such as **importing, cloning, merging, and community sharing**.

---

## 1. Introduction to the Community Packages Tab

**[00:00:00](https://www.youtube.com/watch?v=8FplwKKa708&t=00h00m00s)**

JCB now includes a new tab under **Import JCB Packages** called **Community Packages**. This feature allows developers to share, import, and reuse ready-made JCB packages contributed by the community.

**Purpose:**

* Provides a **quick start** for building components.
* Acts as a **backup repository** for your own packages.
* Enables **reuse of component features**, such as linking Joomla users or field configurations.

Once a package is available in the community directory, you can import it to start new projects without affecting your existing components.

---

## 2. The Clone Feature

**[00:01:17](https://www.youtube.com/watch?v=8FplwKKa708&t=00h01m17s)**

JCB includes a **Clone** function that creates an exact duplicate of an existing component.

**Key points:**

* Cloning generates a new component not linked to the original.
* All **Admin Views**, **Fields**, and related items are duplicated.
* New fields carry a suffix (e.g., `(EO)`) to distinguish them.

This feature complements community package imports by allowing developers to work on new variations safely.

---

## 3. Import Feature and Merge Options

**[00:02:00](https://www.youtube.com/watch?v=8FplwKKa708&t=00h02m00s)**

When importing a JCB package, you can choose whether to **merge** with an existing component or **create a new one**.

* If **Merge = Yes**, the imported data updates existing items.
* If **Merge = No**, JCB creates a new component with independent Admin Views and Fields.

During import, JCB still merges universal items like:

* Validation rules
* Field types
* Snippets
* Language strings

After import, JCB displays a log showing which files were added and which actions occurred. This transparency helps you verify that a **new, isolated component** was created successfully.

---

## 4. Community Sharing and Collaboration

**[00:04:01](https://www.youtube.com/watch?v=8FplwKKa708&t=00h04m01s)**

JCB encourages developers to **share their packages** with the community. Sharing promotes collaboration, speeds up development, and supports open-source contribution.

**Community Repository:**

* Hosted on GitHub under:
  `https://github.com/vdm-io/JCB-Community-Packages`

This repository stores shared JCB packages for others to import directly through the JCB interface.

---

## 5. Forking and Cloning the Repository

**[00:05:06](https://www.youtube.com/watch?v=8FplwKKa708&t=00h05m06s)**

To contribute a package:

1. **Fork** the `JCB-Community-Packages` repository on GitHub.
2. **Clone** your forked version to your development environment.
3. Add your JCB package to your cloned repository.

> 💡 **Tip:**
> You'll need a Linux or compatible environment that supports Bash to run the `hash.sh` script later in this process.

---

## 6. Preparing Your Package for Contribution

**[00:07:13](https://www.youtube.com/watch?v=8FplwKKa708&t=00h07m13s)**

Before sharing:

* Ensure your package is **tested and stable**.
* Avoid sharing incomplete or non-functional components.
* Avoid duplicates—if a similar package exists, contribute improvements instead.

To prepare:

1. In JCB, **export** your component (e.g., `JCB_QuestionsAnswers.zip`).
2. Locate it in your system's **temporal directory**.
3. Move the `.zip` file into your cloned community repository folder.

---

## 7. Running the Hash Script

**[00:14:02](https://www.youtube.com/watch?v=8FplwKKa708&t=00h14m02s)**

In the terminal:

1. Navigate to your cloned repository.
2. Verify untracked files:

   ```bash
   git status
   ```
3. Run the Bash script:

   ```bash
   ./hash.sh
   ```

### Script Requirements

Ensure the following tools are installed:

* `jq`
* `sha1sum`

The script:

* Calculates SHA1 checksums for each `.zip` file.
* Extracts metadata (`info.vdm`) from your package.
* Updates `checksum.json` with package details.

---

## 8. Committing Your Package

**[00:17:30](https://www.youtube.com/watch?v=8FplwKKa708&t=00h17m30s)**

After the script finishes:

1. Stage and commit your files:

   ```bash
   git add .
   git commit -am "Adds Questions and Answers package"
   ```
2. Sign your commits if possible to verify authenticity:

   ```bash
   gpg --sign
   ```
3. Push changes to your forked repository:

   ```bash
   git push origin main
   ```

---

## 9. Creating a Pull Request

**[00:19:54](https://www.youtube.com/watch?v=8FplwKKa708&t=00h19m54s)**

Once your package is committed:

1. Open GitHub, navigate to your fork.
2. You'll see your branch is "1 commit ahead of VDM."
3. Click **"Create Pull Request"**.

Your previous commit message becomes the PR title. Add extra details as needed, especially if:

* Your package includes a **key**.
* Special instructions or testing notes are required.

The JCB admin team reviews and tests all submissions before merging them into the official repository.

---

## 10. Package Visibility and Automatic Updates

**[00:21:30](https://www.youtube.com/watch?v=8FplwKKa708&t=00h21m30s)**

Once your pull request is approved and merged:

* The new package automatically appears in JCB's **Community Packages** tab.
* All users can now **import** it directly from within JCB.

If you encounter issues or want to discuss community packages:

* Open an issue in the **JCB Community Packages** repository.
* Do **not** post these issues in the main JCB repository.

---

## Summary

By following these steps, you can easily share your Joomla Component Builder creations with the community:

1. Export your package from JCB.
2. Fork and clone the community repository.
3. Add your `.zip` file and run the `hash.sh` script.
4. Commit and push your changes.
5. Create a pull request on GitHub.

This system encourages collaboration, accelerates development, and builds a stronger JCB ecosystem.

---
