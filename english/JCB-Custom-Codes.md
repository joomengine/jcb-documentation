# JCB! Custom Codes Overview

Joomla Component Builder (JCB) lets you centralise bespoke logic in **Custom Codes** so that you can reuse, share, and automatically maintain behaviour across multiple components. The feature now covers two complementary workflows:

1. **Reusable code blocks with argument injection** – labelled **JCB (manual)** inside the interface.
2. **Persistent file overrides managed by insert/replace tags** – labelled **Hash (automation)**.

This page summarises both approaches, explains how they interact with other JCB tooling, and links to the deeper tutorials already present in the documentation set.

---

## 1. Reusable Code Injection with `[CUSTOMCODE=...]`

The **JCB (manual)** method lets you define a code fragment once and then inject it anywhere JCB renders code (PHP, XML, JavaScript, HTML, etc.). Reference the fragment with a placeholder such as:

```text
[CUSTOMCODE=mainReadmePackageFooter]
```

To pass dynamic values, append a `+` separated list of arguments:

```text
[CUSTOMCODE=mainReadmePackageFooter+foo,bar,baz]
```

Inside the custom code definition you can reference these values via zero-based placeholders:

* `[[[arg0]]]` → `foo`
* `[[[arg1]]]` → `bar`
* `[[[arg2]]]` → `baz`

> ✅ **Match arguments to placeholders.** If your code references `[[[argN]]]`, you must supply a value for every placeholder when injecting the snippet.

### Encoding reserved characters

Arguments are parsed by JCB, so reserved characters must be HTML encoded before they reach your custom code:

| Character | Encoded form |
| --- | --- |
| `[` | `&#91;` |
| `]` | `&#93;` |
| `,` | `&#44;` |
| `+` | `&#43;` |
| `=` | `&#61;` |

### Scope and limitations

* Manual custom codes can be injected in **any JCB code area** and even **inside other custom codes**.
* They **cannot** be used in their own definition or within **Hash automation** code blocks.
* Argument placeholders are currently one-way; once compiled, the generated project no longer contains the `[[[argX]]]` markers. To update an argument-driven custom code, edit it in the **JCB UI** and recompile.

For a video-led walkthrough of the interface, see [JCB Manual Custom Code](./JCB-manual-custom-code-implementation.md) and [Reuse Custom Code](./Reuse-Custom-Code.md).

---

## 2. Persistent File Overrides with Hash Automation

When the component compiled by JCB lives on the same Joomla instance, you can inject or replace snippets directly inside the generated files. Wrap the target block with special comment tags and JCB will detect, store, and reapply the code on future compilations. Example PHP insert tag:

```php
/***[INSERT<>$$$$]***/
// your code
/***[/INSERT<>$$$$]***/
```

Behind the scenes JCB:

1. Scans your installation for the tag pairs.
2. Extracts the content and saves it in the Custom Code UI.
3. Tracks the file path and the line number context.
4. Re-injects the code whenever you compile again.

Insert/replace automation currently supports **PHP** and **HTML** contexts. If the original location becomes ambiguous, JCB comments out the block, warns you during compilation, and preserves the code so that you can re-home it manually.

Refer to [Automatic Import of Custom Code During Compilation](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) for the full lifecycle, including how hashes are calculated and how to re-trigger updates.

---

## 3. Reverse Engineering Language Strings

When automated imports capture code such as `Text::_('COM_EXAMPLE_LABEL')`, JCB automatically translates the constant back to its human-readable text before displaying it in the editor. This makes it easier to maintain your language strings alongside the code snippets that use them.

---

## 4. Version Control, Forking, and Collaboration

Custom Codes adopt the same Git-friendly workflow that other JCB entities use:

* **Init** – Import the custom code records from a repository.
* **Reset** – Overwrite the local definition with the repository version.
* **Push** – Publish updates when you have write access.
* **Fork** – Maintain a personal or team-specific variant while upstream keeps evolving.

This modular approach encourages teams to share curated sets of reusable snippets and automation rules across multiple projects.

---

## 5. Where to go next

* [TIPS: Custom Code](https://git.vdm.dev/joomla/Component-Builder/wiki/TIPS:-Custom-Code) for the tag syntax reference and edge cases.
* [Reuse Custom Code](./Reuse-Custom-Code.md) to see practical helper patterns.
* [Automatic Import of Custom Code During Compilation](./Automatic-import-of-custom-code-during-compilation-in-JCB.md) for hash automation internals.

Use these guides together to design a workflow that blends reusable snippets and on-disk overrides without losing work between compilations.
