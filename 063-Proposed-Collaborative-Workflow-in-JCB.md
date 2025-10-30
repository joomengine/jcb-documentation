# **Proposed Collaborative Workflow in Joomla Component Builder (JCB)**

This documentation explains how to collaborate effectively on Joomla Component Builder (JCB) projects using a structured workflow that integrates JCB, GitHub, and JCB Packages.
Each section includes timestamps linked to the official tutorial video for deeper reference.

---

## **1. Checked-Out Functionality and Permission Area**

[00:00:00](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h00m00s)

JCB supports collaborative development within a shared Joomla environment. When a user opens a component for editing, the system **locks (checks out)** that item-preventing others from editing it simultaneously. Once saved and closed, the component becomes available again.

This functionality applies to all areas of JCB, including:

* Components
* Admin and Site Views
* Fields
* Layouts

JCB also includes a **comprehensive permissions system**, allowing fine-grained control over who can view, edit, or manage specific areas.
By assigning user groups in Joomla's Access Control List (ACL), you can enable different levels of contribution.

> **Tip:** You can configure permissions for JCB itself under *Components → Component Builder → Options → Permissions.*

---

## **2. Working in an Offline Development Environment**

[00:02:23](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h02m23s)

Although collaborative online environments work well, JCB's preferred setup is a **local (offline) development environment**, such as:

* XAMPP / LAMP stack
* Docker containers
* Virtual machines

Offline development ensures isolation, safety, and speed. However, this limits real-time collaboration.
To solve this, JCB introduces mechanisms for **sharing and synchronizing component data between different developers**.

---

## **3. The "Servers" Area and SFTP Synchronization**

[00:03:13](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h03m13s)

A new JCB feature called **Servers** introduces **SFTP connections**, allowing data exchange between remote JCB instances.
This lays the groundwork for syncing JCB data (like components, views, or fields) between multiple installations - effectively linking teams working on the same component in different environments.

> **Future Goal:** Establish a system where multiple JCB installations automatically synchronize components using secure SFTP transfers.

---

## **4. Development Method Feature**

[00:04:14](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h04m14s)

The **Development Method** (introduced in JCB v2.7.9) adds automation for developers.
Located under *Global Options → Development Method*, this feature includes two modes:

1. **Default:** Traditional manual compiling and installing.
2. **Expansion:** Automatically builds and installs selected components based on cron job frequency.

This automation helps prepare JCB for seamless project synchronization between local and remote installations-essential for distributed teams.

---

## **5. Multi-Developer Collaboration**

[00:06:18](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h06m18s)

The long-term goal is to enable **multiple developers** to work on the same project from their local environments.
Each developer can push their changes (after reaching a stable state) to a shared online JCB hub.
Team members review, test, and merge these changes, just like a Git pull request workflow-but integrated within JCB.

---

## **6. VDM Packages and JCB Package Management**

[00:07:15](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h07m15s)

The **VDM Packages area** in JCB lists all official and community packages available for import.
These include both free and premium component blueprints.
Each package links to:

* **GitHub source code**
* **Joomla installable version**
* **JCB package metadata**

> **Note:** You can import or export JCB packages to share or reuse components.
> Each package represents the **JCB-mapped component**, not the compiled Joomla component.

---

## **7. Understanding the JCB Mapped Component vs. Joomla Component**

[00:08:30](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h08m30s)

* **JCB Mapped Component** - the blueprint containing all data (fields, views, scripts) inside JCB.
* **Joomla Component** - the compiled output of that blueprint.

You can edit JCB Mapped Components to generate updated Joomla Components, but changes made directly to the compiled Joomla Component do not affect the JCB data unless you edit through the integrated IDE custom code system.

---

## **8. Collaborative Example: Questions & Answers Component**

[00:10:26](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h10m26s)

As a practical example, let's use the **Questions & Answers** package.
To collaborate:

1. Go to the package's **GitHub repository** and **fork** it.
2. Clone your fork locally using Git.
3. In your JCB installation, **import** the JCB package version of that component.

You now have both the Git repository and JCB's internal mapping of the component ready for synchronized development.

---

## **9. Setting Up the Local Environment and Git Path**

[00:11:26](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h11m26s)

In JCB:

1. Open *Global Options → Paths*.
2. Set the **Git Repository Folder Path** (e.g., `/home/user/Joomla/Git`).
3. Save your settings.

On your local system, create these directories manually if they don't exist:

```bash
mkdir -p ~/Joomla/Git
```

Add company and language settings as required, and save the configuration.

---

## **10. Compiling the Component and Linking to GitHub**

[00:12:49](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h12m49s)

1. Compile the imported component for the first time.
2. When prompted, choose **"Add to Repository Folder → Yes"**.
   This automatically generates your component's full source structure inside the Git path.
3. Navigate to that directory and initialize Git:

```bash
cd ~/Joomla/Git/com_questions_and_answers_joomla_3
git init
git remote add origin <your_fork_URL>
git pull origin master
```

After this, compiling updates the code automatically.
Run `git status` and `git diff` to see any JCB-driven changes.

---

## **11. XML Compilation Methods in JCB**

[00:21:05](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h21m05s)

Under *Global Options → Compilation*, you can choose between two XML methods:

1. **SimpleXMLElement** (faster but requires PHP extensions)
2. **String Manipulation** (fallback, works on most servers)

> **Recommendation:** Use *String Manipulation* if your server lacks certain PHP modules.

---

## **12. Committing and Pushing Changes**

[00:23:36](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h23m36s)

Once changes are verified:

```bash
git add .
git commit -am "Updated the component with improvements made to JCB"
git push
```

Your fork will now show as *"1 commit ahead"* on GitHub.
Submit a pull request to the original repository for review.

---

## **13. Handling Pull Requests and Review Process**

[00:24:42](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h24m42s)

Before submitting multiple pull requests, coordinate with others to avoid duplication.
Each JCB package managed on GitHub will include a **Pull Request Template** with contributor guidelines.

> **Tip:** Be patient with reviews-community contributions are validated thoroughly for consistency and stability.

---

## **14. Contributing Back to JCB Packages**

[00:27:58](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h27m58s)

After your changes are accepted into the **Joomla Component Repository**, replicate them in the **JCB Package Repository**.

Steps:

1. Fork the **vdm-io/JCB-Packages** repository.
2. Sync your fork with the master branch.
3. Export your updated JCB package.
4. Replace the old package in your fork.
5. Commit and push changes with a reference to the related pull request.

---

## **15. Keeping Forks in Sync**

[00:30:22](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h30m22s)

To keep your fork up to date:

```bash
git remote add upstream https://github.com/original_owner/original_repo.git
git fetch upstream
git checkout master
git merge upstream/master
git push
```

> **Optional:** Use a shell script (like `UpdateForks.sh`) to automate syncing across multiple repositories.

---

## **16. Exporting and Updating JCB Packages**

[00:37:06](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h37m06s)

1. Export your JCB package from within JCB (*Packages → Export*).
2. Move the exported file to your local JCB-Package repository folder.
3. Run your `hash.sh` script if available to regenerate hashes.
4. Commit and push with a reference to the corresponding Joomla Component pull request:

```bash
git commit -am "Updated JCB package with improvements made in JCB ref: vdm-io/joomla-component#1"
git push
```

This links both repositories and ensures traceability between code and JCB data.

---

## **17. Export Key Synchronization and Trust**

[00:38:42](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h38m42s)

Each JCB package uses a **unique export key**, encrypted for security.
To collaborate, developers must use the same key, provided by the package's original author.
Without it, exports won't match or synchronize properly.

> **Important:** Keys are encrypted and never exported in plain text.
> Coordinate directly with the package owner to obtain authorization for shared development.

---

## **18. Completing the Cycle**

[00:44:24](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h44m24s)

Once both pull requests (to the Joomla Component and JCB Package Repositories) are merged:

* Your local and forked versions remain synchronized.
* Other developers can now pull the updated JCB package.
* The entire community benefits from the improvement cycle.

---

## **19. Importing Packages: Clone vs. Merge**

[00:48:00](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h48m00s)

When importing JCB packages:

* **Clone Import:** Creates a copy you can modify independently.
* **Merge Import:** Integrates updates into your existing package.

> **Recommendation:** Use *Merge* for syncing with the community version; use *Clone* for experimentation or forks.

---

## **20. Conclusion**

[00:49:06](https://www.youtube.com/watch?v=zlhFyrCGWik&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&index=63&t=00h49m06s)

The **Collaborative Workflow in JCB** allows multiple developers to:

* Work locally in safe environments.
* Synchronize progress via GitHub and JCB Packages.
* Maintain consistency between JCB Mapped Components and compiled Joomla Components.

As JCB continues evolving, this workflow will strengthen automated validation and speed up community-driven component development.

---
