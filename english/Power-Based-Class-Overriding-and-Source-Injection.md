# Power-Based Class Overriding & Source Injection in JCB

## Overview

Joomla Component Builder (JCB) now allows **Powers** to place PHP classes directly into generated extension `src/` trees for:

- Components
- Modules
- Plugins

This behaviour is deterministic and namespace-driven. JCB decides both the target path and whether the class should **override** an existing generated class or **inject** a new file based on the Power namespace you define.

---

## Core rule: namespace maps to destination

JCB resolves the Power namespace and uses it to determine:

1. **Extension type + area** (Component/Module/Plugin and Administrator/Site)
2. **Path and class name** using dot notation

If the resolved namespace + class name matches a generated class, the Power overrides that file. If it does not match an existing generated class, JCB adds a new file.

---

## Dynamic placeholders for reusable Powers

To make Powers reusable across projects, JCB supports placeholders in namespaces.

### Available placeholders

- `[[[NamespacePrefix]]]` -> the project's namespace prefix
- `[[[ComponentNamespace]]]` -> the project's component namespace
- `[[[Componment]]]` -> the project's component name

> Keep the placeholder spelling exactly as shown above when using this feature.

---

## Component examples

### Override an existing generated component class

Target generated class:

```text
src/Extension/ComponentbuilderComponent.php
```

Power namespace:

```text
[[[NamespacePrefix]]]\Component\[[[ComponentNamespace]]]\Administrator\Extension.[[[Componment]]]Component
```

Result:

- Placeholders are resolved.
- Namespace maps to the generated class.
- `ComponentbuilderComponent.php` is replaced by your Power class.

### Inject a new class into administrator `src/`

Power namespace:

```text
[[[NamespacePrefix]]]\Component\[[[ComponentNamespace]]]\Administrator\MyFolder.MyOwnClass
```

Resulting path:

```text
src/MyFolder/MyOwnClass.php
```

### Inject a new class into site `src/`

Power namespace:

```text
[[[NamespacePrefix]]]\Component\[[[ComponentNamespace]]]\Site\MyFolder.MyOwnClass
```

Resulting path:

```text
site/src/MyFolder/MyOwnClass.php
```

---

## Module examples

### Override module dispatcher

Target generated class:

```text
src/Dispatcher/Dispatcher.php
```

Power namespace:

```text
[[[NamespacePrefix]]]\Module\CPanelRedirect\Administrator\Dispatcher.Dispatcher
```

Result:

- Generated module dispatcher is replaced.
- Power class becomes the active dispatcher.

### Inject a new class into module administrator `src/`

```text
[[[NamespacePrefix]]]\Module\CPanelRedirect\Administrator\MyFolder.MyOwnClass
```

-> `src/MyFolder/MyOwnClass.php`

### Inject a new class into module site `src/`

```text
[[[NamespacePrefix]]]\Module\CPanelRedirect\Site\MyFolder.MyOwnClass
```

-> `site/src/MyFolder/MyOwnClass.php`

---

## Plugin examples

### Override an existing plugin class

Target generated class:

```text
src/Extension/ComponentbuilderPowersAutoloaderCompiler.php
```

Power namespace:

```text
[[[NamespacePrefix]]]\Plugin\Extension\ComponentbuilderPowersAutoloaderCompiler\Extension.ComponentbuilderPowersAutoloaderCompiler
```

Result:

- Generated plugin extension class is replaced.
- Power class becomes the compiled class.

### Inject a new class into plugin `src/`

```text
[[[NamespacePrefix]]]\Plugin\Extension\ComponentbuilderPowersAutoloaderCompiler\MyFolder.MyOwnClass
```

-> `src/MyFolder/MyOwnClass.php`

---

## Dot notation mapping

Inside the final namespace segment, dot notation controls folders and class names.

Example:

```text
MyFolder.SubFolder.MyClass
```

Maps to:

```text
MyFolder/SubFolder/MyClass.php
```

Rule:

- Everything before the last dot becomes folders.
- Everything after the last dot becomes the class name.

---

## Using injected/overridden classes in your project

Once JCB places the Power class in the correct `src/` location, you can use it as a normal extension class and reference it through your existing JPK/custom code workflows.

---

## Important trade-off

This is a deliberate advanced-control feature:

- If you override a generated class, you own that class implementation.
- JCB will not regenerate that class unless the Power override is removed.

Use this when you need explicit architectural control and long-term, source-level customisation.

---

## Why this matters for Superpower Areas

This capability turns JCB Superpower usage into a reliable source-injection system:

- deterministic class placement
- explicit override behaviour
- portable namespace patterns using placeholders
- reusable advanced logic across multiple projects

---

## Source discussion

This document was created from the feature discussion:

- <https://github.com/orgs/joomengine/discussions/1012>
