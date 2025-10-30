# COMPONENT FTP AND MORE

(*Based on [YouTube Video](https://www.youtube.com/watch?v=hzbZlLl-xlA&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)*)
(*Click on timestamps to jump to specific sections in the video.*)

---

## Adding README Script

[00:00:00](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h00m00s)

The **README script** in Joomla Component Builder (JCB) allows you to add a markdown-based introduction page to your component. This file usually serves as your component's **home or landing page** once users access it on GitHub or Joomla's extension manager.

For example, when viewing a component repository on GitHub, the README file displays information such as an image, description, and layout. These are all defined in Markdown format and stored within the component.

To view the raw version of this README file, click **"Raw"** in GitHub - this shows you the exact markdown syntax.
In JCB, you can add both the **README** and **README text** directly inside your component settings.

These sections use **placeholders** (for example: `###version###`) that automatically pull dynamic information from the component's metadata.

---

## Placeholders

[00:01:10](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h01m10s)

The `#` symbol in markdown indicates a **header** (H1-H6). It's essential to understand basic Markdown syntax when editing the README script.

Within the JCB README text area, placeholders such as `###version###`, `###author###`, or `###component_name###` are automatically replaced by their actual values during compilation.

If you update your component's version, these placeholders will automatically reflect the new version - no need for manual edits.

---

## Component-Builder Link Back Info

[00:01:59](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h01m59s)

The **link-back section** in JCB's README allows you to provide **helpful resources** or **community links**.
Here you can include:

* Links to **help menus** or documentation
* Installation instructions
* Community or contribution information

Although this section isn't required, it's encouraged to leave the link-back information in place to help others discover and support the JCB project. This ensures the broader community continues to grow and stay connected.

---

## Markdown Reference

[00:02:46](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h02m46s)

For guidance on Markdown syntax, refer to the official documentation:
[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)

---

## Admin and Site Views - Adding or Editing

[00:03:06](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h03m06s)

In the **Admin View** and **Site View** sections of JCB, you can:

* Create **new views** for your component.
* **Edit existing** admin or site views.

> **Important:**
> Creating a new Admin View here does **not automatically link** it to your component.
> To link it, go to the component's **Settings → Admin Views** area and select the views you want associated.

This interface simply provides a quick way to manage related admin and site views from within the component editor.

---

## FTP Info - Updating Components

[00:03:57](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h03m57s)

The **FTP Server settings** allow automatic deployment of your compiled component to your remote server and to set up **Joomla update server support**.

### Joomla Update Server Integration

Joomla uses an **update server** to inform users when new versions are available.
In JCB, if you set the **Update Server** to **Yes**, the compiler will automatically include this information in the component's XML manifest file.

If set to **No**, the update server will be omitted.

### FTP Configuration

To enable automatic uploads, configure the following fields in your component's **FTP settings**:

* **FTP Host:** Your server's domain or IP address.
* **Port:** Default FTP port is `21`.
* **Username / Password:** Credentials with write access to your component's target folder.
* **Binary Type:** Usually `15` or `21` (JCB default).

When compiling, JCB logs into your FTP server, uploads the compiled component ZIP to the specified folder, and then disconnects automatically.

---

## FTP Info - Sales Server

[00:06:32](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h06m32s)

The **Sales Server** works similarly to the update server, but serves a different purpose:

* **Update Server:** Notifies users of available updates.
* **Sales Server:** Hosts and provides access to the **component ZIP package** for sale or distribution.

You can host this on your own web server or through a service such as **WHMCS**.
Create an FTP account pointing directly to the folder that stores your distributable ZIPs.

When compiling, if **"Add backup folder"** and **"Save sales server"** are both set to **Yes**, JCB will:

* Move the compiled ZIP file to the Sales Server folder.
* Create a backup copy locally.

---

## Global Options and Encryption

[00:07:49](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h07m49s)

Global options define key paths and encryption settings for JCB.
You can access these in **Joomla → Components → Component Builder → Options**.

### Encryption

Some fields, like FTP credentials, are **encrypted** for security.
You'll see an encryption key field in the Global Settings.

* When you add your own encryption key, JCB encrypts stored data (like FTP details).
* Changing this key later will make it **impossible to decrypt** existing data.

If changed, all encrypted information (such as FTP credentials) must be re-entered.

> **Note:** JCB supports two encryption types:
>
> * **Basic Encryption (Basic Key)** - default and sufficient for FTP and credentials.
> * **Advanced Encryption** - for more complex data protection needs.

---

## Folder Paths and Git Integration

[00:09:13](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h09m13s)

### Compiler and Custom Folders

* These paths are system-dependent and not flexible.
* It's best to **leave them blank** unless absolutely necessary.

### Backup and Git Folders

* **Backup Folder:** Used for local component backups.
* **Git Folder:** Used for version control repositories.

When compiling, JCB will:

1. Generate all component files in the **Git folder** (uncompressed).
2. Replace older files with updated ones (Git will track file changes).
3. Leave your Git repository intact - only modified files are updated.

You can then push the folder to **GitHub**, **GitLab**, or any Git server.

> **Tip:** If you're new to Git, explore beginner courses on [Lynda.com](https://www.google.com/search?q=lynda.com+courses) or Udemy.

---

## FTP Folder Access Rules

[00:11:18](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h11m18s)

Ensure the FTP account used connects **directly** to the folder where JCB should upload component ZIPs.
Subfolders are **not supported**.

During compilation, JCB's FTP process logs in, places the file, and disconnects.
These FTP credentials correspond to the folder path accessible from your Joomla installation.

---

## Compiler.PHP - FTP Functions

[00:12:32](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h12m32s)

In the backend, JCB's compiler file (`compiler.php`) includes specific functions for managing FTP transfers.

### Key Functions

* **`moveFileToFTPServer()`** - Transfers compiled ZIP to the configured FTP destination.
* **`getFTP()`** - Checks for existing FTP connections and loads relevant credentials.

These functions utilize Joomla's **FTP Client Library (`/libraries/joomla/client/ftp.php`)**.
They securely handle host, port, username, and password during file transmission - ensuring no sensitive data is exposed.

---

## Update Server - Versioning and SQL Updates

[00:14:23](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h14m23s)

The **update server XML file** defines all released versions and their corresponding download links.

### Version Management

When releasing updates, consider:

* What **new views or fields** have been added.
* Whether **database structure changes** are needed.

If your new version modifies the database, you can use the **Version Updates** feature in JCB to attach an **SQL script** to that version.

Example:

* Version **1.2.9** requires a table alteration.
* Add your SQL command (using Joomla conventions such as `#__table_name`).
* JCB will execute it during the update process.

Each version must have:

* The **update SQL dump** (if needed).
* The **download link** for the updated ZIP.
* Version numbers that **increment logically**.

> **Example:**
>
> * `1.2.9` → `1.3.0` → `1.3.1` → `1.3.2`
>   The latest version in the list must match the current version set in the component.

You can host updates on any platform - **GitHub**, **Bitbucket**, or your custom URL.

---

## Conclusion

[00:18:26](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h18m26s)

This concludes the overview of **Component FTP and More** within Joomla Component Builder.
We've covered how to:

* Add and manage the README markdown script
* Configure Admin and Site Views
* Set up FTP for deployment and updates
* Use Sales and Update Servers
* Manage Global Options and Encryption
* Configure Folder Paths and Git integration
* Understand Versioning and SQL update handling

Once you've set up your component, you are ready to proceed with **building the front-end site views**.
Remember: Always start with admin views, then move to site views for a complete Joomla component structure.

[00:19:06](https://www.youtube.com/watch?v=hzbZlLl-xlA&t=00h19m06s)
