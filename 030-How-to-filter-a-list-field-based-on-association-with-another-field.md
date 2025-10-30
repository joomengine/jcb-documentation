# How to Filter a List Field Based on Association with Another Field

**Tutorial Duration:** ~20 minutes
**Source:** Joomla Component Builder (JCB) Video Tutorial
**Applies to:** Latest JCB version (Admin and Site View workflow)

---

## Overview

In many Joomla components, you may need to **filter the options of one list field based on another field's value**.
A common use case is limiting the **Region** list to only show the regions belonging to a selected **Country**.

This guide demonstrates how to achieve this dynamically in **Joomla Component Builder (JCB)** using a combination of:

* JavaScript
* Ajax (Model + Controller)
* PHP in the backend

You will learn how to connect two related fields, fetch data via Ajax, and dynamically update dropdowns without page reloads.

---

## 1. Understanding the Filtering Goal

**Timestamp:** [00:00:00](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h00m00s)

The objective is to **limit a dropdown (list) field** based on another field's value - for example:

* When selecting a **Country**, only the corresponding **Regions** are loaded.
* When a Country is **unselected**, the Region field should also reset.

This enhances usability and ensures data consistency.

---

## 2. Example Scenario: Country and Region in "Job Tracking" Component

**Timestamp:** [00:00:43](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h00m43s)

Example setup:

* Component: **Job Tracking**
* Admin Views: `Country` and `Region`
* Client View: Uses both fields in a related form.

When creating or editing a client:

* Selecting a country loads only its related regions.
* If a country has no regions, a "Create a Region" option appears.
* If the country does have regions, it shows "Select a Region."

---

## 3. JavaScript Implementation

**Timestamp:** [00:04:30](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h04m30s)

To enable dynamic dropdown updates, add custom JavaScript that handles:

1. Data storage of all regions
2. Ajax requests to fetch filtered regions
3. UI updates on Country selection

### 3.1. Define the Variables

```javascript
var regions = {}; // Object storing all available regions
var region = '';  // Holds the currently selected region (if any)
```

When the page loads, all regions are parsed into the `regions` variable.
Later, only those belonging to the selected country will be reinserted into the dropdown.

---

### 3.2. Show the Loading Indicator

**Timestamp:** [00:06:23](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h06m23s)

To improve UX, show a loader while the dropdown updates:

```javascript
jQuery("#loading").show();
```

This class can use Joomla's built-in spinner or your custom loader.

Then, clear existing options from the Region list before repopulating:

```javascript
regionField.find('option').remove();
regionField.trigger('liszt:updated');
```

> **Note:** `liszt:updated` is a legacy Chosen plugin trigger used by Joomla list fields.
> Future versions may use `chosen:updated`.

---

### 3.3. Fetch Filtered Regions with Ajax

**Timestamp:** [00:07:51](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h07m51s)

Define the `getRegion()` function to send the Ajax request:

```javascript
function getRegion(countryId) {
  if (!countryId) return;

  jQuery.ajax({
    type: "POST",
    url: "index.php?option=com_jobtracking&task=getRegion",
    data: { country: countryId },
    success: function(result) {
      setRegion(result);
    }
  });
}
```

Once the response is received, it calls `setRegion()` to update the dropdown.

---

### 3.4. Updating the Region Dropdown

**Timestamp:** [00:09:38](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h09m38s)

The `setRegion()` function populates the Region field:

```javascript
function setRegion(data) {
  jQuery.each(data, function(i, id) {
    if (regions[id]) {
      regionField.append('<option value="' + id + '">' + regions[id] + '</option>');
    }
  });
  regionField.trigger('liszt:updated');
}
```

If no regions exist for a country:

* Display "Create a Region"
* Optionally, open the modal to create one

```javascript
var select_a_region = "Select a Region";
var create_a_region = "Create a Region";
```

---

### 3.5. Handle Button Functionality

**Timestamp:** [00:12:22](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h12m22s)

If your list field includes a "Create" or "Edit" button:

* Ensure the JS function name follows JCB's naming convention:
  `regionButton()` if your field name is `region`.
* Run a correction routine if necessary after repopulating the list.

---

### 3.6. Detect Field Changes

**Timestamp:** [00:14:06](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h14m06s)

Automatically update the Region list whenever the Country changes:

```javascript
adminForm.on('change', '#jform_country', function() {
  var countryId = jQuery(this).val();
  getRegion(countryId);
});
```

This ensures `getRegion()` runs both on page load and field change.

---

## 4. PHP Backend: Ajax Model and Controller

**Timestamp:** [00:15:13](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h15m13s)

In JCB, Ajax requests are handled through a **centralized Ajax model** and **controller**.

### 4.1. Ajax Controller

Defines the accepted input and the task:

```php
$input = $this->input->get('country', 0, 'INT');
$this->task = 'getRegion';
```

### 4.2. Ajax Model Method

In the Ajax model (`models/ajax.php`):

```php
public function getRegion() {
    $countryId = (int) $this->input->get('country', 0);
    $db = Factory::getDbo();
    $query = $db->getQuery(true)
        ->select($db->quoteName('id'))
        ->from($db->quoteName('#__regions'))
        ->where($db->quoteName('published') . ' = 1')
        ->where($db->quoteName('country') . ' = ' . $db->quote($countryId));
    $db->setQuery($query);
    return $db->loadColumn() ?: false;
}
```

This returns an array of region IDs related to the selected country.

> **Tip:** Adjust table and column names according to your own component.

---

## 5. Custom Field Setup in JCB

**Timestamp:** [00:18:34](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h18m34s)

Both the **Country** and **Region** fields are **Custom List Fields** created in JCB.

### Field: Region

* **Type:** List
* **Button:** `True` (to allow "Create" option)
* **Source Table:** Regions
* **Dynamic Label:** Can use PHP in XML definition for field label or description

You can add inline PHP in the XML or within the "Type PHP" area of the field definition.

> **Best Practice:**
> Keep most logic in the Admin View (JavaScript + Ajax),
> and use the custom field XML only for defining structure and relationships.

---

## 6. Final Result

**Timestamp:** [00:20:15](https://www.youtube.com/watch?v=Z8FLifQOjUk&t=00h20m15s)

When implemented correctly:

* Selecting a country dynamically filters the region dropdown.
* Ajax ensures seamless updates.
* The same pattern can be applied to **any related fields** - e.g., Categories → Subcategories, Brand → Models, etc.

---

## 7. Summary

| Step   | Description                                                 |
| ------ | ----------------------------------------------------------- |
| **1.** | Create two related custom list fields (Country & Region)    |
| **2.** | Add Ajax method (`getRegion`) to the model and controller   |
| **3.** | Write JS functions (`getRegion`, `setRegion`) in Admin View |
| **4.** | Attach JS listener for Country field changes                |
| **5.** | Optionally manage "Create Region" button behavior           |
| **6.** | Compile and install your component                          |

---

## Helpful Tips

* Always sanitize input and validate returned data.
* Use consistent naming for fields (e.g., `country`, `region`) to avoid confusion.
* JCB compiles all Ajax methods into one file (`models/ajax.php`) - no need to manually add multiple controllers.
* If targeting another component's table, ensure you know the association field name.

---

**End of Tutorial**
**Video Reference:** [How to Filter a List Field Based on Association with Another Field](https://www.youtube.com/watch?v=Z8FLifQOjUk)

---
