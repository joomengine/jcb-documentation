# How to Use the File Field Type to Upload a File in JCB

### Overview

This guide explains how to correctly use the **File Field Type** in Joomla Component Builder (JCB) to enable file uploads in your component. You'll learn how to add and configure the file field, implement server-side validation and movement, and display the uploaded file dynamically in the admin view.

---

## 1. Adding a File Field to a Component

**Timestamp:** [00:00:00](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h00m00s)

We begin by adding a file upload field to a component. In this example, the **Demo Component** is used, which includes several Admin Views such as `Look`, and Site Views like `Looks` and `Looking`.

We'll add our **file field** to the `Look` Admin View.

> **Note:** JCB doesn't automatically handle file uploads due to security concerns. You'll implement this logic manually to maintain full control.

---

## 2. Using the Existing File Fieldtype

**Timestamp:** [00:01:06](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h01m06s)

JCB already provides a **File** fieldtype. Navigate to:

> `Component Builder → Fieldtypes → File`

Here, you'll see the field attributes as defined in Joomla's documentation. Review the available options like:

* **Accept**
* **Size**
* **Multiple**
* **Directory**

> The **Accept** parameter (e.g., `image/*`) specifies the file types allowed for upload.

If this parameter is missing in your version, add it manually.

---

## 3. Adding the "Accept" Attribute (Optional Update)

**Timestamp:** [00:02:30](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h02m30s)

If your JCB version lacks the `accept` attribute:

1. Add it manually under "Size".
2. Set its default value to `image/*`.
3. Provide a description (e.g., "Allowed file types").

Save and close the fieldtype.

---

## 4. Creating and Configuring the File Field

**Timestamp:** [00:03:19](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h03m19s)

Go to:

> `Component Builder → Fields → New`

Set the following:

* **Name:** `banner`
* **Label:** `Banner`
* **Type:** `File`
* **Description:** "Upload an image from your computer (max 100KB)."

Save and close.

---

## 5. Assigning the File Field to an Admin View

**Timestamp:** [00:04:54](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h04m54s)

1. Open your component's Admin View (`Look`).
2. Click on **Fields**.
3. Add the new field `Banner (file)` under the desired **tab** (e.g., "More").
4. Set **Alignment** to *Full Width*.
5. Save and close.

> **Tip:** Avoid duplicate field names. Each field should have a unique `Name` to prevent history tracking issues.

Compile and install your component, then verify that the field appears correctly.

---

## 6. Understanding Why the File Isn't Uploaded Yet

**Timestamp:** [00:09:56](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h09m56s)

When saving an item, you'll notice the file isn't uploaded to your server yet.
That's because JCB doesn't include **server-side upload logic** by default. You'll need to:

* Validate the file
* Move it to the desired folder
* Check and sanitize it
* Save its path to the database

---

## 7. Adding Server-Side File Handling Code

**Timestamp:** [00:11:27](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h11m27s)

Open your component's **Model** file in your IDE:

```
administrator/components/com_demo/models/look.php
```

Locate the `save()` function. This is where form data is processed.
You'll insert your file handling logic here.

---

### 7.1 Inspecting Input Data

Use a quick debug:

```php
var_dump($data);
var_dump($input->files->get('jform'));
```

This reveals what file data Joomla receives during the form submission.

---

### 7.2 Copy Joomla's Upload Handling Function

**Timestamp:** [00:16:58](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h16m58s)

Find and copy the `getPackageFromUpload` function from:

```
/administrator/components/com_installer/models/install.php
```

Rename it to something like:

```php
public function myUploadFunction($input)
```

Modify it to:

* Handle image uploads (`jpg`, `jpeg`, `png`, `gif`)
* Skip zlib/unzip logic
* Include checks for upload size and type
* Use `JFile::upload($tmp_src, $tmp_dest, false, true)` to move the file

---

### 7.3 Add Validation and Cleanup

* Create a helper function `checkUpload()` to validate the file type.
* Add a `removeFile()` function to delete files that fail validation.

Example (simplified):

```php
public function removeFile($path)
{
    jimport('joomla.filesystem.file');
    if (JFile::exists($path)) {
        JFile::delete($path);
    }
}
```

---

## 8. Moving the File to Its Final Location

**Timestamp:** [00:37:14](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h37m14s)

Once validation passes, move the file from the Joomla temporary folder to a permanent directory:

```php
JFile::move($tmp_dest, JPATH_ROOT . '/images/' . $filename);
```

Save the relative file path (`/images/filename.jpg`) into the database field.

---

## 9. Adding Custom PHP to JCB

**Timestamp:** [00:46:09](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h46m09s)

Back in JCB:

1. Open your Admin View (`Look`).
2. Go to **Custom Buttons** → **PHP (Model Method)**.
3. Paste your helper functions (`myUploadFunction`, `checkUpload`, `removeFile`) here.
4. In **Add PHP (save method - before data modelling)**, insert:

   ```php
   $package = $this->myUploadFunction($input);
   $data['banner'] = $package['dir'] . '/' . $package['name'];
   ```

Save your changes.

---

## 10. Displaying the Uploaded File in the Admin View

**Timestamp:** [00:50:13](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h50m13s)

To preview the uploaded image in the edit form:

1. In the same Admin View, add the following in **Add JavaScript (view-footer)**:

   ```php
   <?php if (isset($this->item->banner) && is_string($this->item->banner)) : ?>
   <script>
       jQuery(document).ready(function() {
           jQuery('#jform_banner').after('<img src="<?php echo $this->item->banner; ?>" class="preview-banner" alt="Banner Preview" />');
       });
   </script>
   <?php endif; ?>
   ```

2. Add styling via **Add CSS (view)** to format the image preview neatly.

Recompile and reinstall your component.

---

## 11. Testing the Result

**Timestamp:** [00:58:59](https://www.youtube.com/watch?v=o482sK4DxkM&t=00h58m59s)

1. Open the Admin View (`Look`).
2. Upload a file and click **Save**.
3. The file should now:

   * Upload successfully
   * Move to `/images/`
   * Store its path in the database
   * Display in the form after saving

> If you change the image, the new one replaces the preview, but you may still need to manually remove the old file (custom logic can automate this).

---

## 12. Conclusion

**Timestamp:** [01:00:11](https://www.youtube.com/watch?v=o482sK4DxkM&t=01h00m11s)

You've now implemented a working **File Field Upload System** within JCB using Joomla's native capabilities.
For reference, you can find the final PHP upload logic as a GitHub Gist provided by the tutorial author.

> **Tip:** For enhanced security, validate the MIME type using Joomla or PHP image functions.
> For broader upload support (e.g., PDFs), adjust the allowed extensions in your `checkUpload()` logic.

---

### Key Takeaways

* Always implement server-side validation for uploads.
* Use `JFile` and `JFolder` classes to move and clean files securely.
* Add helper methods to keep your model clean and reusable.
* Use JCB's **Custom PHP sections** to safely include custom logic during compilation.
