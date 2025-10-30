# JCB Fields Type Extended

*(Based on the tutorial: "JCB Custom Fields Type Extended")*  
*(Click timestamp links to open the corresponding YouTube segments.)*  

---

## Introduction

[00:00:00](https://www.youtube.com/watch?v=91iIAuHZj38&t=00h00m00s)  
This tutorial provides a detailed walkthrough of how **Custom Field Types** work in Joomla Component Builder (JCB). While previous tutorials introduced basic field concepts, this updated explanation reflects improvements made in JCB's newer versions - both in interface design and compiler behavior.

Custom Fields are among the most flexible and powerful field types in JCB, enabling you to connect data across tables, create dynamic relationships, and even add custom button actions that interact directly with other views.

---

## Understanding Custom Fields

### What Are Custom Fields?

[00:01:31](https://www.youtube.com/watch?v=91iIAuHZj38&t=00h01m31s)  
Custom Fields allow you to **connect one table to another** - linking data between views. They can build one-to-one or one-to-many relationships and generate dynamic lists that pull data from other tables.

They're not just dropdowns; they can become the backbone of interrelated component structures. Because of their flexibility, Custom Fields are often used for entity linking, dynamic select options, or interactive field types.

---

## Joomla Concept of Custom Fields

[00:02:24](https://www.youtube.com/watch?v=91iIAuHZj38&t=00h02m24s)  
Custom Fields are rooted in Joomla's own field system. In your component's **`models/fields/`** folder, each field type corresponds to a PHP file defining its behavior.

When JCB compiles your component, it creates these files automatically - for example, `preachers.php` - and ensures the XML form references them via the `<addfieldpath>` directive.

```xml
<addfieldpath path="administrator/components/com_example/models/fields" />
