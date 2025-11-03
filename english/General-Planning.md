# **General Planning: Joomla Component Builder**

### Video Reference

[Watch Tutorial on YouTube](https://www.youtube.com/watch?v=gEgwiVNj6N0&list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE)

---

## **1. Be Prepared to Build Components**

[00:00:00](https://youtu.be/gEgwiVNj6N0?t=0)

Before building with Joomla Component Builder (JCB), preparation is key. You should:

* Understand **what your component will do**.
* Plan the **database structure** you want to set up.
* Know how your tables and fields will **map to each other**.

Revisit the [JCB! Fields overview](./JCB-Fields.md) before you start modelling—its breakdown of schema, rendering, validation, and repository workflows will help you translate requirements into reusable field definitions.

> **Tip:** A clear data map will help you define views, relationships, and field connections correctly in JCB.

If you are new to database design, review basic **table relationships** (one-to-many, many-to-many) to ensure your component logic aligns with Joomla's MVC structure.

---

## **2. Using Demo Components as Learning Tools**

[00:00:49](https://youtu.be/gEgwiVNj6N0?t=49)


This tutorial uses **Sermon Distributor**, a demo component, to illustrate the building process.
By studying it, you'll learn:

* How **backend views** connect to the database.
* How naming and structuring components affects consistency.

Each backend view in Joomla is **tightly bound to its database table**. Plan accordingly.

---

## **3. Understanding the Purpose of Conventions**

[00:01:40](https://youtu.be/gEgwiVNj6N0?t=100)


JCB allows flexibility but follows established **implementation conventions** for a reason:

* These ensure smooth integration with Joomla's MVC system.
* Breaking conventions may lead to issues or the need to rebuild sections later.

> **Recommendation:** Follow JCB's default naming and structure conventions unless you fully understand their implications.

---

## **4. Backend Views and Database Connections**

[00:02:16](https://youtu.be/gEgwiVNj6N0?t=136)


Backend views form the **core link** to your database tables.
For example, in *Sermon Distributor*:

* A **list view** shows multiple sermons.
* An **edit view** allows editing of individual sermons.

Both share the same database table but represent different entry points.

> The backend connects to and manages the database; the frontend presents data dynamically.

---

## **5. Dynamic Get and Data Relationships**

[00:04:44](https://youtu.be/gEgwiVNj6N0?t=284)


The **Dynamic Get** feature is central to data handling in JCB. It:

* Connects backend and site views.
* Retrieves and maps data models from database fields.
* Can be reused in multiple contexts.

Think of it as a bridge between database structure and your component's dynamic output.

---

## **6. Mapping Views to Database Tables**

[00:05:40](https://youtu.be/gEgwiVNj6N0?t=340)


Backend views in JCB **map directly to the database**.
Each field defined in JCB corresponds to a column in the database.
This direct mapping ensures Joomla's controllers, models, and classes behave correctly.

If you require data from external or third-party tables, JCB offers **Custom Backend Views** that act more dynamically, similar to frontend views.

> **Example Use Case:** Creating a dashboard or report view that aggregates data from multiple tables.

---

## **7. Using Dynamic Get for Combined Data**

[00:09:19](https://youtu.be/gEgwiVNj6N0?t=559)


You can create a **custom backend view** that uses the *Dynamic Get* feature to pull data from multiple related tables (e.g., sermons, preachers, series, and downloads).

A practical example is creating an *Analysis* view to:

* Combine data across multiple tables.
* Model and present data dynamically in charts or lists.

---

## **8. Structuring Fields and Data Mapping**

[00:13:05](https://youtu.be/gEgwiVNj6N0?t=785)


Before you start, **map out your fields**:

* Sermons → name, preacher, series, files
* Preachers → name, email, description, website
* Series → name, description, statistics
* Files → filename, counter, sermon reference

> **Tip:** This planning phase prevents structural errors and simplifies view creation.

---

## **9. Adding Compulsory Fields**

[00:15:20](https://youtu.be/gEgwiVNj6N0?t=920)


In JCB, compulsory fields are marked with an asterisk (*).
When creating a new component:

1. Add the required fields (e.g., *name*, *image*).
2. Set the **component image** (recommended size: *300x300px*).
3. Save before proceeding to view creation.

---

## **10. Adding and Creating Views**

[00:16:20](https://youtu.be/gEgwiVNj6N0?t=980)


There is a difference between:

* **Adding views** - attaching existing views to your component.
* **Creating views** - defining new ones from scratch.

You add views via the **Settings tab** of your component.

---

## **11. Adding Fields to Views**

[00:16:44](https://youtu.be/gEgwiVNj6N0?t=1004)


Each view must have fields associated with it.
You cannot add a field to a view unless the field exists in your JCB configuration.

Common reusable fields:

* **Name** (can be reused across multiple views)
* **Hits** (automatically added by default)

---

## **12. Admin Views and Field Creation**

[00:19:11](https://youtu.be/gEgwiVNj6N0?t=1151)


After setting up your component, proceed to create **Admin Views**:

1. Go to **Admin Views → New**.
2. Enter base information (title, table name, etc.).
3. Create and attach fields - avoid duplicates.
4. Mark **custom fields** when linking related data (e.g., preacher IDs).

Custom fields allow you to pull IDs or values from another view's dataset, like *Preachers* or *Series*.

---

## **13. Creating Normal vs Custom Fields**

[00:21:54](https://youtu.be/gEgwiVNj6N0?t=1314)


In Joomla:

* **Normal fields** are standard data entries.
* **Custom fields** link dynamically to another view or table.

Custom fields rely on your backend structure; ensure your base fields are ready before defining them.

---

## **14. Planning Your Component**

[00:22:51](https://youtu.be/gEgwiVNj6N0?t=1371)


Effective component building requires **planning before development**.
Map your database tables, define view relationships, and identify shared fields.

Paper planning or flow diagrams can help visualize:

* Component structure
* Data relationships
* Reusable fields

> This pre-planning prevents confusion and speeds up implementation in JCB.

---

## **15. What's Next**

[00:23:50](https://youtu.be/gEgwiVNj6N0?t=1430)


Next, the tutorial series covers:

* Creating and managing **field types**.
* Building **admin and site views**.
* Making your component **fully functional**.

Understanding this planning phase ensures you can build structured, maintainable Joomla components efficiently.

---

### **Key Takeaways**

* Plan database tables and views **before** opening JCB.
* Use **Dynamic Get** to fetch and reuse structured data.
* Backend views map **directly to tables**, while custom views can aggregate data.
* Follow **JCB conventions** to maintain compatibility.
* Always **create fields first**, then add them to views.

---
