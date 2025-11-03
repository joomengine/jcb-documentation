# General Overview of How Community Snippets Work in Joomla Component Builder

This guide explains how the **Community Snippets system** works in **Joomla Component Builder (JCB)**. The new system introduces a **community concept**, allowing users to **share, import, and maintain** code snippets collaboratively within the JCB ecosystem.

> **Video Tutorial:** [Watch on YouTube](https://www.youtube.com/watch?v=qr4I1jeCp7I&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

## 1. Introduction: The New Community Snippet Concept

[00:00:00](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h00m00s)

The **Snippet Manager** in JCB now supports community contributions.
Originally, Snippets were only local assets you could reuse within:

* Custom Admin Views
* Site Views
* Templates
* Layouts

Now, with the community feature, you can share and import Snippets from the JCB community repository.

---

## 2. The New Snippet Area

[00:00:50](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h00m50s)

The Snippets interface shows:

* **Type** of snippet (e.g., Common, Layout)
* **Name** of the snippet
* **Library** it belongs to (e.g., *UiKit v2*)

Selecting a Snippet displays:

* The snippet's **type**, **library**, and **name**
* A **link** to the library's external documentation (if available)

This helps identify and reuse snippets efficiently during development.

---

## 3. Local vs Community Snippets

[00:01:29](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h01m29s)

Two snippet types now exist:

* **Local Snippets** - Created and stored on your own system.
* **Community Snippets** - Shared through the public JCB Snippet Repository.

You can now **contribute** your snippets or **import** those shared by others.

---

## 4. Contributing Snippets and Contributor Details

[00:01:56](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h01m56s)

Each snippet includes **contributor information**:

* Name
* Email
* Website

When you create a new snippet, JCB automatically fills in your contributor details (set in **Global Options → Company Tab**).

You can't edit contributor details of existing snippets - those are fixed to maintain credit integrity.

> **Tip:** If contributor names are missing, update your contributor database under *Snippets → Contributor Area*.

---

## 5. Matching Snippet Metadata

[00:03:58](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h03m58s)

Ensure your snippets are **mapped the same way** as the community's:

* **Name**
* **Type**
* **Library**

These three fields form the **unique identifier**.
If you rename or alter them, JCB treats your snippet as *new* instead of *updated*.

---

## 6. Getting and Sharing Snippets

[00:04:48](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h04m48s)

Use the **"Get Snippets"** area to:

* **Share** your local snippets with the community.
* **Download** snippets shared by others.

When you click **"Share Snippets"**, JCB:

1. Packages your selected snippets.
2. Stores them at `/media/host/Dropbox/sandbox/joomla/tmp/snippets.zip`.

---

## 7. Helper Resources

[00:05:33](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h05m33s)

For assistance:

* [Git Quick Start (Udemy)](https://www.udemy.com/git-quick-start/)
* [JCB Snippet Tutorials (YouTube)](https://www.youtube.com)
* [Open GitHub Issues](https://github.com/vdm-io/Joomla-Component-Builder-Snippets/issues)

These resources help you learn version control, forking, and pull requests.

---

## 8. How "Get Snippets" Works

[00:06:07](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h06m07s)

When you click **Get Snippets**:

* JCB connects to the **GitHub Snippet Repository**.
* Loads all community snippets via **Ajax**.
* Displays them in categories such as *Equal*, *Out of Date*, *New*, *Diverged*, and *Ahead*.

You can view the repository directly on GitHub.

---

## 9. Snippet Status Categories

### a. Equal (In Sync)

[00:06:55](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h06m55s)
Indicates your local snippet matches the community version exactly.

### b. Out of Date

[00:07:22](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h07m22s)
Appears when a community version has been improved or updated.
You can import the new version to stay current.

### c. New

[00:07:57](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h07m57s)
Lists snippets that exist in the community but not locally.
Click **"Get Snippet"** to import them into your JCB.

### d. Diverged

[00:08:49](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h08m49s)
Occurs when both your local and community versions have been modified differently.
You can choose to **revert** to the community version.

### e. Ahead

[00:09:18](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h09m18s)
Means your local snippet is newer.
You can either keep your version or revert to the community one.

---

## 10. Bulk Tools

[00:10:05](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h10m05s)

The **Bulk Update Tool** helps you:

* Fetch all **new** or **ahead** snippets at once.
* **Revert** all outdated snippets in bulk.

This is useful when many community snippets have been added or changed.

---

## 11. Snippet Details and Contributor Recognition

[00:10:57](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h10m57s)

Each snippet includes:

* **Description**
* **Usage example**
* **Code preview**
* **Contributor information**

### Blame View

[00:11:12](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h11m12s)
Displays who modified each part of the snippet.
Minor edits are shown here instead of replacing the main contributor.

Contributors can link their profiles or websites to gain visibility within the JCB community.

---

## 12. Snippet Usage in JCB

[00:12:52](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h12m52s)

Snippets can be inserted into:

* **Custom Admin Views**
* **Site Views**
* **Templates**
* **Layouts**

After importing new snippets, they appear at the bottom of your local list and include the contributor details automatically.

---

## 13. Dynamic Contributor Fields

[00:13:38](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h13m38s)

If contributor details are missing, JCB automatically uses your **global company details**.

When you create a new snippet:

1. JCB checks if a snippet with the same *Name*, *Type*, and *Library* exists.
2. If not, it assigns your details as the contributor.
3. If yes, it retains the original contributor's data.

---

## 14. Sharing Updated Snippets

[00:15:48](https://www.youtube.com/watch?v=qr4I1jeCp7I&t=00h15m48s)

When you've created or improved snippets:

1. Select them in the list.
2. Click **Share Snippets** to generate a shareable package.
3. Follow tutorials on **forking** and **pull requests** to submit them to the community.

---

## 15. Summary

The Community Snippet System enhances collaboration within JCB by enabling:

* **Contribution** of new snippets
* **Synchronization** with community updates
* **Recognition** of contributors
* **Seamless sharing** via GitHub integration

By maintaining and contributing snippets, developers collectively improve the JCB ecosystem.

---
