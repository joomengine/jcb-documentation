# **Drag and Drop Upload Functionality in Joomla Component Builder (JCB)**

## **Overview**

**Video Source:** [VDM Tutorials - Drag and Drop Upload Functionality in JCB](https://www.youtube.com/watch?v=UvzDyVQyHDI)
This guide explains how to build a dynamic drag-and-drop file uploader within JCB's component structure, including server-side Ajax handling, automated image cropping, and secure file storage.

---

## **1. Introduction to the Drag-and-Drop Functionality**

**[00:00:00](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h00m00s)**
This tutorial demonstrates the **Drag and Drop Automated Crop Functionality**, which complements the standard JCB **File Field Type**.

While the File Field is simpler, this method adds:

* Dynamic upload with Ajax
* Image cropping
* Better UX through UIkit components

---

## **2. Setting Up the Front-End Upload with UIkit**

**[00:01:13](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h01m13s)**

### **Step 1: Choose a UI Library**

JCB supports multiple front-end libraries.
For this tutorial, **UIkit v2** is used (though you can replace it with Bootstrap or UIkit v3).

> **Tip:**
> Navigate to **UIkit v2 → Components → Upload** to review official upload documentation.

---

## **3. Adding HTML and JavaScript for Drag and Drop**

**[00:03:20](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h03m20s)**

The HTML defines the drop zone and status messages; the JavaScript handles upload progress and Ajax calls.

You can add this markup and script inside a **Custom Code Note** within your JCB Admin View.

Example structure:

```html
<div id="upload-drop-main-documents" class="uk-placeholder">
  <p>Drop files here or <a class="uk-form-file">select one</a></p>
  <div id="progressbar-main-documents" class="uk-progress uk-hidden">
    <div class="uk-progress-bar" style="width: 0%;"></div>
  </div>
</div>
```

> **Dynamic Options:**
>
> * The **upload URL** changes dynamically based on single/multiple file mode.
> * Accepted file types are passed from component parameters.
> * Ajax enables file uploads before saving the main record.

---

## **4. Handling Unsaved Items**

**[00:05:40](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h05m40s)**

When a file is uploaded but the item has **no ID yet**, JCB stores the uploaded filename in a **hidden form field**.
Once the item is saved, the file data is automatically bound to that record.

---

## **5. Importing the Required JCB Packages**

**[00:06:21](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h06m21s)**

Before building the uploader, import the **VDM Packages** that include the **Document Manager** component:

1. Go to **Joomla Components → Import Components**.
2. Select **VDM Packages** tab.
3. Fetch from GitHub → Verify Checksum → Import.

> The system confirms "**Package PASSED checksum validation!**"

---

## **6. Setting Allowed File Formats**

**[00:12:03](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h12m03s)**

Navigate to your **Component → Options → Media Tab**, then define:

* **Allowed Document Formats** (e.g., PDF)
* **Allowed Media Formats** (e.g., MP3)
* **Allowed Image Formats** (e.g., JPEG)

Set desired **crop dimensions** (e.g., width=200, height=350) for image resizing.

---

## **7. Demonstrating the Upload in Action**

**[00:13:11](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h13m11s)**

The interface now shows dynamic upload areas:

* "Upload your Image"
* "Upload your Documents"
* "Upload your Media"

Allowed formats and dimensions are displayed automatically, drawn from global configuration.

> All uploaders (images, documents, media) are handled through reusable JavaScript snippets.

---

## **8. Understanding the JavaScript Snippets**

**[00:22:01](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h22m01s)**

The main snippet is `uikitFileUploader`, which:

* Gets allowed formats dynamically.
* Uses `JRouter` to route Ajax calls correctly for both Admin and Site views.
* Updates the DOM with progress bars and allowed file types.

Each uploader (document, image, media) uses the same script, changing only the passed arguments.

---

## **9. Security and Encryption Layers**

**[00:30:21](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h30m21s)**

To protect uploads:

* Use **Medium Encryption (local-file-key)** for safer storage.
* Files behind the `/public_html` folder cannot be accessed directly.
* Only authorized users can download or remove uploads.

---

## **10. Server-Side Ajax Implementation**

**[00:51:28](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h51m28s)**

In the component's **Admin View (Documents)**, add a **Custom Code Area** named `phpAjaxUploader`.

The PHP logic:

1. Validates allowed views and formats.
2. Moves uploaded files to the correct folders.
3. Generates secure, randomized filenames.
4. Optionally resizes images using a helper class (`resizeImage`).
5. Encrypts file metadata before saving.

---

## **11. Creating Component Configuration Fields**

**[00:54:48](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h54m48s)**

To add configurable upload formats:

1. Go to **Settings → Create Component Config**.
2. Add **List Fields** for document, image, and media formats.
3. Enable "Allow Multiple Selection".

These configuration values are later fetched dynamically by the uploader scripts.

---

## **12. Functions Breakdown**

### **uploadFile**

**[00:57:45](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h57m45s)**

* Validates the uploading view and file type.
* Uses `getPackageFromUpload()` to process uploaded files.
* Returns Ajax response with filename and success state.

### **uploadNow**

Handles moving files and triggers:

* Image resizing (if applicable).
* Encryption for document/media files.
* Database updates via Ajax.

### **setFileNameArray**

**[01:10:47](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=01h10m47s)**
Used for handling multiple uploads when the item already exists (has an ID).

### **removeFile**

**[01:12:53](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=01h12m53s)**
Validates user permissions and deletes files from both server and database.

---

## **13. Demonstrations**

### **Uploading an Image**

**[00:43:18](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h43m18s)**
Drag an image into the drop zone - it uploads, crops, and displays instantly.

### **Uploading a Document**

**[00:44:51](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h44m51s)**
Drag and drop PDFs; links are generated for download.

### **Uploading Media Files**

**[00:48:17](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h48m17s)**
Upload multiple MP3 files simultaneously; Ajax saves them directly to the database.

---

## **14. Download and Controller Integration**

**[00:46:57](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=00h46m57s)**
A custom **Controller task** (`download`) manages secure file downloads using encrypted URLs.

---

## **15. Summary**

**[01:16:52](https://www.youtube.com/watch?v=UvzDyVQyHDI&t=01h16m52s)**

This advanced drag-and-drop upload system provides:

* Real-time Ajax uploads
* Automated cropping and resizing
* Secure, encrypted file handling
* User-friendly interaction
* Modular reuse through custom snippets

> **Note:** This is an advanced implementation requiring solid knowledge of **JavaScript, PHP, and JCB architecture**. Debugging and adaptation for your component are necessary.

---

## **16. Key Advantages**

* Users never interfere with each other's uploads.
* Enhanced UX compared to Joomla's native Media Manager.
* Full control over formats, cropping, and storage paths.

---

## **17. Helpful Links**

* **UIkit Upload Documentation:** [https://getuikit.com/v2/docs/upload.html](https://getuikit.com/v2/docs/upload.html)
* **VDM GitHub Snippets:** [https://github.com/vdm-io](https://github.com/vdm-io)
* **Joomla Component Builder:** [https://joomlacomponentbuilder.com](https://joomlacomponentbuilder.com)

---
