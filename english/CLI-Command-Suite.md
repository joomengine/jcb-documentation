# CLI Command Suite

> Source discussion: [CLI Command Suite · joomengine · Discussion #1013](https://github.com/orgs/joomengine/discussions/1013)

The Joomla Component Builder (JCB) CLI introduces a complete, production-grade command-line interface that lets you manage, synchronize, compile, install, and distribute JCB assets without using the GUI.

This CLI layer is not a wrapper or shortcut — it is a first-class interface to JCB’s internal systems and repositories.

---

## Design goals of the JCB CLI

The CLI was designed to:

- Enable full automation of JCB workflows
- Support remote repositories as first-class citizens
- Allow headless usage (CI/CD, servers, containers)
- Provide deterministic, scriptable behavior
- Mirror (and in some cases extend) GUI functionality
- Maintain explicit control (nothing happens implicitly)

---

## How to access the CLI

From your Joomla root directory:

```bash
php cli/joomla.php
```

This lists all available Joomla CLI commands, including the Component Builder command group.

To see help for any command:

```bash
php cli/joomla.php <command> -h
```

---

## CLI command naming structure

All JCB CLI commands follow this structure:

```text
componentbuilder:<action>:<area>
```

### Actions

- `compile`
- `get`
- `init`
- `pull`
- `push`
- `reset`

### Areas

Areas represent JCB-managed entity types, such as:

- `joomla_component`
- `joomla_module`
- `joomla_plugin`
- `power`
- `field`
- `fieldtype`
- `layout`
- `template`
- `snippet`
- `library`
- `repository`
- `admin_view`
- `site_view`
- `custom_code`
- `dynamic_get`
- `validation_rule`
- `class_extends`
- `class_method`
- `class_property`
- `placeholder`
- `joomla_power`
- …and others

The behavior of an action is consistent across all areas — only the target entity changes.

---

## The action model (how the CLI thinks)

The CLI is intentionally action-driven, not state-driven.

Each action has a specific meaning.

---

## `get` – Synchronize existing items

### Purpose

Synchronize items that already exist locally with their remote repositories.

### Command example

```bash
php cli/joomla.php componentbuilder:get:joomla_component
```

### What `get` does

- Fetches updates from remote repositories
- Synchronizes metadata and content
- Does not force overwrite
- Does not initialize missing items

### Inputs

```text
--items / -i       CSV, newline-separated, or JSON list
--items-file       Path to file containing items
```

### Key behavior

- Items do not have to be GUIDs
- Aliases may be resolved internally (when supported)
- Designed for safe synchronization

### When to use `get`

- Updating existing local assets
- Keeping local state in sync
- Non-destructive refresh

---

## `init` – Initialize from a remote repository

### Purpose

Initialize and synchronize items that do not yet exist locally.

### Command example

```bash
php cli/joomla.php componentbuilder:init:joomla_component
```

### What `init` does

- Pulls items from a remote repository
- Creates local tracking state
- Optionally overwrites existing items
- Can resolve aliases to GUIDs

### Additional inputs

```text
--repo / -r        Repository JSON object
--repo-file        Path to repository definition
--force / -f       Force overwrite
--resolve          Resolve non-GUID identifiers
```

### When to use `init`

- First-time setup
- Cloning assets from another project
- Bootstrapping a local environment

---

## `pull` – Force remote state locally

### Purpose

Forcefully synchronize local state from remote, overwriting local changes.

### Key characteristics

- Destructive to local changes
- Always favors remote source
- Intended for recovery or enforcement

### When to use `pull`

- Resetting local divergence
- Enforcing canonical remote state
- CI environments

---

## `push` – Publish to a remote repository

### Purpose

Push local items and their dependencies to a remote package repository.

### Command example

```bash
php cli/joomla.php componentbuilder:push:joomla_component
```

### What `push` does

- Uploads items to a repository
- Automatically resolves dependencies
- Blocks until operation completes
- Requires valid GUIDs

### Important notes

- Dependencies are detected automatically
- Partial pushes are not allowed
- Intended for publishing and sharing

---

## `reset` – Reset local tracking state

### Purpose

Reset JCB’s internal tracking for specific items.

### What reset means

- Clears local sync metadata
- Does not delete the item
- Forces re-initialization on next `init`/`pull`

### Safety guarantees

- Requires explicit item list
- Will not run with empty input
- Cannot be executed accidentally

---

## Compiler command (most powerful command)

### Command

```text
componentbuilder:compile:component
```

This command exposes the full JCB compiler through CLI.

### What the compiler CLI can do

- Compile one or multiple components
- Pull missing components automatically
- Inject Powers
- Apply repository rules
- Minify output
- Insert placeholders
- Target multiple Joomla versions
- Auto-install compiled extensions
- Integrate with backup and sales servers

---

## Component selection

At least one component input is required:

```text
--component / -c
--components
--components-file
```

All formats support:

- CSV
- Newline-separated values
- JSON arrays
- `@/path/to/file` shorthand

---

## Options bundle system

The compiler supports an options bundle:

```text
--options / -o
```

This allows:

- JSON objects
- External files
- Merged configuration
- CLI flags override file values

This makes the compiler ideal for:

- CI pipelines
- Reproducible builds
- Shared configuration

---

## Auto install (`-i`)

```text
-i, --install
```

When enabled:

- Compiled extensions are automatically installed
- Works for Components, Modules, and Plugins
- Requires a valid Joomla environment

---

## Powers integration

```text
-p, --powers
--powers-repository
```

Controls:

- Whether Powers are injected
- Whether Power repositories are synchronized
- Whether Power overrides are applied

This directly integrates with the Power override system documented separately.

---

## Target Joomla version

```text
-j, --joomla-version
```

Allowed values:

- `3`
- `4`
- `5`
- `6`

This controls:

- Namespace structure
- API compatibility
- Output behavior

---

## Environment variable support

Every major option supports environment variable fallbacks, including:

```text
JCB_COMPILE_COMPONENT
JCB_COMPILE_COMPONENTS
JCB_COMPILER_OPTIONS
JCB_COMPILE_INSTALL
JCB_JOOMLA_VERSION
JCB_POWERS
JCB_MINIFY
...
```

This allows:

- Headless execution
- Docker usage
- CI/CD integration
- Secrets isolation

---

## Verbosity and output control

```text
-v    Normal output
-vv   Verbose
-vvv  Debug
-q    Quiet
```

Output uses Symfony Console styles and respects ANSI settings.

---

## How all areas fit together

Every area (fields, layouts, powers, snippets, etc.) uses:

- The same action logic
- The same input patterns
- The same repository mechanics

Once you understand one area, you understand them all.

---

## Mental model summary

Think of the JCB CLI as:

- A repository-aware asset manager
- A compiler frontend
- A deployment tool
- A synchronization engine

All driven by explicit commands, never by hidden state.

---

## Beta status & testing

The CLI is currently Beta.

Known focus areas:

- Memory usage in large projects
- Long-running compile jobs
- Edge-case dependency graphs

This is why testing and feedback are essential.

---

## Final notes

This CLI is designed to scale:

- From solo developers
- To teams
- To automated pipelines

If you prefer GUIs, you can keep using them.
If you prefer terminals, JCB is now fully at home there too.
