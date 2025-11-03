# Upgrading Joomla 3 + JCB 3 Sites to Joomla 5 + JCB 5

Upgrading long-running projects from Joomla 3 and Joomla Component Builder (JCB) 3.x to the modern Joomla 5 and JCB 5.x stack requires a phased approach. This guide consolidates the legacy JCB 2.5.8/2.6.0 migration videos with the current Joomla 5 upgrade path so you can confidently move production sites without losing data or custom code.

The process is broken into preparation, conversion, core upgrades, and post-upgrade validation. Follow the checklists in order—each stage assumes the previous one has been completed and verified.

---

## 1. Review the upgrade scope and prerequisites

Before changing anything, understand what is going to move and what will stay behind.

* JCB 5.x no longer supports Joomla 3. Your site must land on Joomla 5 (or 6 when released) for ongoing updates.
* Repeatable fields in JCB 3 must be converted to subforms and dedicated tables. This was first introduced in the JCB 2.5.8/2.6.0 releases and remains a prerequisite for modern versions.
* Ensure you have administrator access to Joomla, SSH/FTP credentials, and database access for backups.

> **Checklist**
> 1. Audit installed extensions and note any Joomla 3-only packages.
> 2. Confirm PHP 8.1+ availability—the minimum for Joomla 5.
> 3. Schedule a maintenance window that covers database backups, file backups, and validation time.

---

## 2. Back up and stage the Joomla 3 site

Always work from a copy of production. Use your preferred backup solution or manually export the database (`mysqldump` or phpMyAdmin) and archive the web root. Restore the backup on a staging server that matches your target PHP version.

Once staging is online:

1. Disable cron jobs and third-party integrations that could change data during the upgrade.
2. Enable Joomla's debug logging to capture deprecation notices and SQL errors.
3. Document any template overrides or manually written custom code—they may require adjustments after the upgrade.

---

## 3. Convert repeatable fields to subforms in JCB 3

The oldest JCB 3 installations still rely on repeatable fields. Before upgrading JCB itself, run through your component schema and convert every repeatable field to the newer subform layout:

1. Update the staging site to the latest JCB 3 package available to Joomla 3 users.
2. Inside JCB, open each admin view that contains repeatable fields. Use the conversion tools introduced in JCB 2.5.8/2.6.0 to migrate those fields into subforms. The scripts create dedicated database tables and adjust the admin view XML automatically.
3. Recompile the component and install it on the staging site to verify the converted views.
4. Review Dynamic GET configurations—clean up joins and filters flagged by the migration scripts.

Do not proceed until every component compiles successfully without repeatable field warnings.

---

## 4. Prepare the codebase for Joomla 4 and 5

Joomla only supports incremental major upgrades. Move through the versions in order:

1. Upgrade Joomla 3 to the latest 3.10 release and resolve any warnings on the Pre-Update Check page.
2. Install Joomla 4 on staging using the built-in updater. Reapply your template overrides and confirm that the site loads as expected.
3. After Joomla 4 is stable, run the Joomla 5 upgrade. Verify that all extensions—including JCB—show as compatible.

Throughout this process, clear Joomla's cache and your browser cache between steps to prevent stale assets from masking issues.

---

## 5. Install JCB 5.x and update your components

Once Joomla 5 is running:

1. Install the latest JCB 5 package through the Joomla extension manager.
2. Run the JCB database update check to ensure all schema changes are applied.
3. Open each component in JCB to trigger the new admin layout. Review tabs, subforms, and translation settings—JCB 5 reorganizes these areas compared to JCB 3.
4. Recompile your components and install the generated packages on the staging site. Pay attention to compiler logs for deprecated code references.

If you maintain custom repositories or shared snippets, synchronize them so that new field definitions and library changes propagate to all projects.

---

## 6. Validate multilingual and translation settings

JCB 5 ships with an integrated translation checker and improved language package support. After recompiling:

1. Open the Translation Checker inside JCB and ensure your components meet the required completion percentage.
2. Verify that language strings render correctly in both the backend and frontend.
3. Update language overrides or translation files if keys changed during the upgrade.

---

## 7. Final verification and production rollout

Before going live:

1. Run Joomla's database fix and clear caches.
2. Test frontend and backend workflows, including dynamic GET-driven lists, custom admin tabs, and custom code triggers.
3. Confirm that user permissions, menu items, and modules behave as expected.
4. Take a fresh backup of the upgraded staging site, then repeat the process on production.

Document any manual clean-up or code adjustments so the rest of the team knows how to maintain the new stack.

---

## 8. Troubleshooting tips

* **Dynamic GET conflicts** – Re-save each GET after the upgrade so JCB rewrites its joins with the new schema helpers.
* **Compiler errors** – Clear the `/tmp` directory and rebuild. If problems persist, reinstall the latest JCB package to refresh compiler templates.
* **Translation checker warnings** – Adjust the required completion percentage or finish missing strings before shipping.
* **Admin view layout issues** – Reapply the subform conversion scripts; fields that were skipped the first time can still be migrated manually.

If you encounter issues that are not covered here, capture the error logs and consult the JoomEngine discussion board for community guidance.
