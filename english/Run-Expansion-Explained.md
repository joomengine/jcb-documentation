# Run Expansion Explained

**Tutorial Reference:** [Run Expansion Explained (YouTube)](https://www.youtube.com/watch?v=ozp6m12Fj0o)

---

## Introduction

The **Run Expansion** feature in Joomla Component Builder (JCB) is a powerful and efficient tool designed to **compile and install multiple components simultaneously**. This feature is especially useful for developers managing several interdependent JCB components that share code, classes, or libraries.

This documentation explains how to **enable, configure, and use** the Run Expansion method, along with practical examples and best practices.

---

## 1. Understanding the Run Expansion Feature

**Timestamp:** [00:00:13 → 00:00:34](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h00m13s)

When you click the **Run Expansion** button in JCB, it may initially display an error such as:

> "Expansion failed. Please check your settings in the Global Options of JCB under the Development tab."

This occurs because the feature needs to be properly configured before use.

### Purpose of Run Expansion

Run Expansion allows developers to:

* Compile and install multiple components at once.
* Automate build processes across related projects.
* Speed up iterative development and testing workflows.

---

## 2. Enabling Expansion in Global Options

**Timestamp:** [00:00:34 → 00:00:56](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h00m34s)

Before using the feature:

1. Navigate to **JCB → Global Options**.
2. Open the **Development Tab**.
3. Locate the switch labeled **Expansion**.
4. Set it to **Enabled**.

This toggle activates the Run Expansion system and reveals additional configuration options for controlling its behavior.

> **Tip:** Read the documentation text within this tab carefully. It provides inline explanations of expansion behavior and how it interacts with JCB's development workflow.

---

## 3. Why Expansion Exists

**Timestamp:** [00:00:56 → 00:02:01](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h00m56s)

In complex development setups, you might have multiple JCB components that:

* **Share code** or **reuse classes** across projects.
* Require **simultaneous recompilation** after shared updates.
* Depend on each other to remain in sync during development.

Traditionally, this required compiling and installing each component manually - one at a time.

Run Expansion automates this by allowing you to select several components and compile + install them in one go.

---

## 4. Using Run Expansion

**Timestamp:** [00:02:01 → 00:04:04](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h02m01s)

### Step-by-Step Usage

1. **Select Multiple Components**

   * In the JCB Components view, check all components you wish to compile and install together.

2. **Set Expansion Parameters**

   * You can define:

     * Whether to **move components to the backup folder**.
     * Whether to **copy them to the repository folder**.
     * Whether to **show custom placeholder messages** in output.
     * Whether to **display full logs** of completed actions.

3. **Run Expansion**

   * Click **Run Expansion** from the toolbar.
   * If properly configured, JCB will automatically:

     * Compile each selected component.
     * Install them directly into your Joomla environment.
     * Clean up temporary build files.

> **Pro Tip:** This feature can be linked to a **cron job** for automated background builds - ideal for continuous integration setups.

---

## 5. API Permissions and Access

**Timestamp:** [00:04:04 → 00:04:51](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h04m04s)

If you receive an **"Access Denied"** message when running expansion, it means:

* The Expansion process runs through JCB's **API system**.
* The **API user** executing the command does **not have sufficient permissions**.

### How to Fix

1. Go to the **API configuration** in JCB.
2. Select a **user account** with sufficient privileges:

   * Must have permission to **compile and install components**.
3. Save and try running Expansion again.

This ensures the expansion process can successfully access and manipulate the components on your site.

---

## 6. Performance Comparison

**Timestamp:** [00:05:07 → 00:05:28](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h05m07s)

When comparing traditional manual compilation to Run Expansion:

* Manual process: Compile → Install → Repeat for each component.
* Expansion process: Compiles and installs **all selected components at once**.

This significantly reduces development time.

Additionally:

* Expansion **does not retain the built package** (it is deleted after installation).
* It logs all performed actions:

  * Which components were compiled.
  * Which were installed.
  * Any errors or skipped actions.

---

## 7. Future Applications of Expansion

**Timestamp:** [00:05:52 → 00:06:21](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h05m52s)

While the current use case focuses on **multi-component compilation**, the JCB development team envisions future extensions for:

* **Collaborative development** (team-based integrator concepts).
* **Remote expansion workflows** where builds are synchronized across distributed systems.
* **Continuous build chains** for shared JCB projects.

---

## 8. Default Behavior and Safety

**Timestamp:** [00:06:21 → 00:06:44](https://www.youtube.com/watch?v=ozp6m12Fj0o&t=00h06m21s)

By default:

* The **Expansion Method is disabled**.
* Clicking the **Run Expansion** button will show a message:

  > "Expansion method is disabled. Please enable it in Global Options."

This prevents accidental activation and safeguards against unintended multi-component compilations.

> **Recommendation:** Only enable Expansion when you explicitly understand its purpose and intend to use it.

---

## 9. Conclusion

The **Run Expansion** feature in Joomla Component Builder streamlines complex development workflows involving multiple interdependent components. It offers:

* Faster build and installation cycles.
* Centralized control via API.
* Future scalability for advanced automation.

If you do not require it, you can safely ignore it. But for power users managing interconnected systems, **Run Expansion** can dramatically boost productivity.

---

### Summary Table

| Feature           | Description                                              |
| ----------------- | -------------------------------------------------------- |
| **Purpose**       | Compile and install multiple components at once          |
| **Location**      | Global Options → Development Tab                         |
| **Requirements**  | Enabled Expansion toggle, API user with permissions      |
| **Outputs**       | Installed components, log messages, no package downloads |
| **Default State** | Disabled                                                 |
| **Future Use**    | Integration for team workflows & automated builds        |

---
