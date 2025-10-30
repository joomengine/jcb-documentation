# Automated Backup System in Joomla Component Builder

**Tutorial Video:** [Watch on YouTube](https://www.youtube.com/watch?v=GUWZaODo_IM&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)
(*Click on the timestamps to jump to the video segments*)

---

## 1. Overview of the Automated Backup Feature

[00:00:00](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h00m00s)

The automated backup system is part of JCB's **Extension API**, enabling operations via a URL request - including creating a full backup of your JCB components.

The API extension introduces new automation possibilities. The first implemented feature is the **automated backup**, which allows exporting and securely storing your components either manually or via a CronJob.

> **Note:** JCB's development community is discussing additional API features on GitHub.

---

## 2. The Backup Button and Core Function

[00:01:07](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h01m07s)

JCB already includes a **component export** function. The backup system extends this by adding automation.

* A **Backup** button has been added for manual triggers.
* The same process can also run automatically through a **CronJob**.

When triggered, JCB:

1. Exports all your components (except those in the trash).
2. Encrypts them.
3. Stores them locally in a backup folder.
4. Emails the encryption key to your configured secure email address.

> Only *published*, *unpublished*, or *archived* components are included. Trashed items are ignored.

---

## 3. New Configuration Tabs and Features

[00:02:40](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h02m40s)

To support the backup system, several new configuration tabs have been added in **JCB > Options**:

* **Mail Configuration**
* **DKIM Settings**
* **CronJob**
* **API User**

These settings control how backups are created, secured, and delivered.

---

## 4. API User Setup

[00:03:09](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h03m09s)

The **API User** is the account identity used to authorize the automated backup process.

* When you manually trigger a backup, JCB checks permissions based on the logged-in user.
* When automated via CronJob, it uses the configured API User.

> **Best Practice:**
> The API User should have **full permissions** to all components, fields, and views within JCB.
> This prevents partial or restricted backups caused by permission limits.

Future JCB updates may expand this user-based permission model, ensuring secure access control even for automated tasks.

---

## 5. CronJob Configuration

[00:06:17](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h06m17s)

In the **CronJob tab**, you can find guidance for setting up automatic execution.

The system supports both `curl` and `wget` requests.

* If your server supports `curl`, JCB uses it automatically.
* If not, it falls back to `wget`.

If neither command works, you can manually call the provided **CronJob URL** on your server.

When triggered successfully:

* A green confirmation message appears - "Backup completed and email sent."
* This output may optionally be logged in future versions.

> **Tip:** If your site uses a firewall (e.g., RSFirewall), you may need to configure the request to behave like a normal browser request. Refer to related StackOverflow discussions for `curl` adjustments.

---

## 6. Backup Folder and Encryption Details

[00:08:36](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h08m36s)

By default, backups are saved to a **local folder**.
Future versions will allow remote storage (e.g., FTP servers) for enhanced redundancy.

> **Important:** Joomla does not encrypt configuration fields by default. Store sensitive details (e.g., backup keys) securely.

---

## 7. Email Delivery of Backup Key

[00:09:13](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h09m13s)

The encryption key used for the backup is automatically emailed to the configured address.
Ensure this email is **secure** and **accessible only to trusted administrators**.

---

## 8. Package Naming and Retention Strategy

[00:09:33](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h09m33s)

Backups are named dynamically using timestamps:

* Default: overwrites daily backups.
* Add hour placeholders: retains hourly versions.
* Add minute placeholders: retains every backup instance.

This naming convention lets you manage how frequently older backups are replaced.

---

## 9. Mail Configuration and DKIM

[00:10:13](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h10m13s)

In the **Mail Configuration tab**, you can choose between:

* Joomla's **Global Mail Configuration**, or
* A custom **SMTP setup** for backup emails.

> Always use **SMTP with SSL/TLS** for secure transmission of backup keys.

### DKIM Support

[00:10:54](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h10m54s)
Enabling **DKIM (DomainKeys Identified Mail)** adds an extra layer of authenticity and trust to your outgoing backup emails.

---

## 10. Company Details

[00:11:10](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h11m10s)

Fill out **Company Details** under JCB's Global Configuration.
These details become part of the backup metadata and appear when restoring the package.

Ensure the following are set before saving:

* Company Information
* CronJob Settings
* Backup Folder Path
* Email Settings
* API User

---

## 11. Setting the Export Key

[00:12:10](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h12m10s)

Before running a backup:

* Ensure at least one component has an **Export Key** set.
* If multiple components include keys, JCB combines them into a single encryption key (hashed for security).

The actual encryption key (emailed to you) is derived from these component keys.

---

## 12. Running a Manual Backup

[00:13:07](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h13m07s)

You can initiate a manual backup using the **Backup** button.
When complete, a confirmation message appears.

To verify:

1. Check the backup folder for the new ZIP file.
2. Confirm receipt of the encryption key email.
3. Open the ZIP file to verify all expected files are present - including custom folders if applicable.

> **Tip:** Always use a secure email account with SSL/TLS-enabled SMTP for receiving the encryption key.

---

## 13. Testing the Backup and Restore Process

[00:15:35](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h15m35s)

To validate your backup:

1. Delete an existing component (move it to Trash and empty it).
2. Go to **Import Components**.
3. Select the backup directory.
4. Click **Get File**, then **Continue**.
5. Enter the **encryption key** from your email.
6. Proceed to import.

During the import, JCB displays:

* **Package Owner Details**
* **Components Being Imported**

Once complete, the component is restored.

---

## 14. Verifying Restoration

[00:17:40](https://www.youtube.com/watch?v=GUWZaODo_IM&t=00h17m40s)

To confirm success:

1. Open the **Compiler**.
2. Select the restored component.
3. Compile and install it.
4. Check that all fields, views, and settings are intact.

> You have now successfully configured, automated, and tested JCB's backup and restore process.
