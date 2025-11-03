# Setup Local Development Environment with OctoJoom

> **Video Reference:** [OctoJoom walk-through](https://www.youtube.com/watch?v=owpxKie0I7s)
> **Project Documentation:** [git.vdm.dev/octoleo/octojoom](https://git.vdm.dev/octoleo/octojoom)

OctoJoom is a shell script that provisions Joomla! using the official Docker images, Traefik as the reverse proxy, and Docker Compose files that are generated for you. It replaces the legacy Bitnami-based approach with a repeatable, scalable workflow that mirrors how we build projects today. OctoJoom keeps every local site isolated while still letting you run many Joomla installations at once—perfect for working on multiple JCB projects.

---

## 1. Why OctoJoom?

OctoJoom automates the routine chores of bootstrapping and maintaining your development stack:

* **Official Joomla containers** – each project runs on the images maintained by the Joomla team.
* **Traefik-powered routing** – human-friendly domain names are mapped automatically to the right containers.
* **Reusable environment variables** – OctoJoom writes `.env` files for Docker Compose and Traefik, prompting you only when values are missing.
* **Task-driven workflow** – commands such as `setup`, `enable`, `disable`, or `update` keep day-to-day operations simple.
* **Multi-site friendly** – spin up and manage any number of Joomla projects on the same workstation without port conflicts.
* **Cross-platform** – works on Linux distributions and macOS. Windows users can run it in an Ubuntu (or similar) virtual machine.

> **Tip:** OctoJoom is linted with ShellCheck and designed for terminal use. If you omit CLI options, the script interactively gathers the required details.

---

## 2. Prerequisites

Make sure the following are available on your workstation before installing OctoJoom:

1. **Operating system** – Ubuntu/Debian or macOS. (Use a Linux VM when developing from Windows.)
2. **Docker Engine and Docker Compose plugin** – install from your OS package manager or Docker's official instructions.
3. **Traefik requirements** – OctoJoom configures Traefik for you, but ensure port 80 (HTTP) is free. If another web server is running locally, stop it before you start OctoJoom-managed sites.
4. **Hostname resolution** – add project domains to `/etc/hosts` (e.g., `127.0.0.1 jcb.test`) if you are not using a local DNS solution.

---

## 3. Install OctoJoom

Install the script globally so you can run `octojoom` from any terminal:

```bash
sudo curl -L "https://raw.githubusercontent.com/octoleo/octojoom/refs/heads/master/src/octojoom" -o /usr/local/bin/octojoom
sudo chmod +x /usr/local/bin/octojoom
```

Update later with:

```bash
octojoom --update --access-token <your_git_vdm_access_token>
```

You can uninstall at any time:

```bash
octojoom --uninstall
```

---

## 4. Explore the Help Menu

Run the help command to review all switches:

```bash
octojoom --help
```

Key options you will use frequently:

* `--type` – specify what you are working with (`joomla` or `openssh`).
* `--task` – choose the action (`setup`, `enable`, `disable`, `update`, etc.).
* `--domain` / `--sub-domain` – define the hostnames Traefik will route.
* `--key` – label used for Docker Compose project names.
* `--env-key` – uppercase prefix used when OctoJoom writes environment variables.
* `--joomla-version` – pick the Joomla tag to pull (defaults to the latest stable version if omitted).

If you skip a flag, OctoJoom asks for the value interactively and stores it in the relevant `.env` file so that future commands reuse it.

---

## 5. Create Your First Joomla Site

OctoJoom creates everything you need—Docker networks, Traefik configuration, environment files, and the Joomla container. Start with the `setup` task:

```bash
# Basic interactive setup
octojoom --type joomla --task setup
```

During the setup, provide the domain, sub-domain, key, and Joomla version. OctoJoom saves these details in `.env` files inside its project directory.

You can also supply the values in one command to avoid prompts:

```bash
octojoom --type joomla --task setup \
  --key "mysite" \
  --env-key "MYSITE" \
  --domain "example.local" \
  --sub-domain "jcb" \
  --joomla-version "5.1"
```

What happens next:

1. Docker Compose files are generated for Traefik and your Joomla container.
2. OctoJoom ensures the Traefik proxy is running.
3. A Joomla container is created with bind mounts for persistent storage.
4. `.env` files are written (or updated) with the settings you supplied.

When the command finishes, open your browser to the chosen domain (for example, `http://jcb.example.local`). Complete Joomla's web installer if prompted, then log in to the administrator interface.

---

## 6. Manage Multiple Sites

Every site you create gets its own directory under the OctoJoom workspace. Traefik handles the routing, so each domain can be active simultaneously without clashing on ports. Useful commands include:

* **Enable a site**
  ```bash
  octojoom --type joomla --task enable --container "jcb.example.local"
  ```
* **Disable a site**
  ```bash
  octojoom --type joomla --task disable --container "jcb.example.local"
  ```
* **Reconfigure a site** – rerun `--task setup` to adjust domain names or change Joomla versions. OctoJoom reuses existing data volumes unless you explicitly remove them.

To check which containers are running, use Docker commands such as `docker ps` or read OctoJoom's status output after each task.

---

## 7. Environment Files and Customisation

OctoJoom maintains several `.env` files (for example, one for Traefik and one per site). The script tells you where each file lives when it updates a value. You can open them in your editor to tweak advanced settings such as:

* Extra Traefik labels or middlewares.
* Custom Joomla admin email/password values.
* Additional Docker volumes for development tooling.

Because these files feed Docker Compose, any edits take effect the next time you enable the site.

---

## 8. Install Joomla Component Builder (JCB)

Once the Joomla container is online:

1. Visit the administrator area (e.g., `http://jcb.example.local/administrator`).
2. Navigate to **System → Install → Extensions**.
3. Install Joomla Component Builder from your local package or the Joomla Extension Directory.
4. Import demo packages if needed and continue with your usual JCB workflow.

All Joomla data lives inside the container's persistent volumes, so you can rebuild or upgrade the container without losing your work.

---

## 9. Updating and Maintaining Your Stack

* **Update OctoJoom itself:** `octojoom --update --access-token <token>`
* **Pull newer Joomla images:** rerun `octojoom --type joomla --task setup --joomla-version <tag>` and OctoJoom will fetch the specified image.
* **Remove a site:** disable it first, then delete the project's directory and associated Docker volumes if you no longer need the data.
* **Log files:** check the container logs with `docker compose logs` inside the site's directory when troubleshooting.

---

## 10. Summary

OctoJoom gives you a consistent, containerised workflow for local Joomla and JCB development:

* Install the script once.
* Use `setup` to launch new projects in minutes.
* Manage many sites simultaneously without conflicts.
* Leverage Traefik for tidy, memorable domain names.

Switching from Bitnami to OctoJoom keeps your local environment aligned with modern Docker practices and the tooling we use internally.
