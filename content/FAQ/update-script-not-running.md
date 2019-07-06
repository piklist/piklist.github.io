---
title: "Update script not running"
description: "Fix update script issues."
weight: 15
---

Piklist allows you to easily create [update scripts](/updates/) that run on certain versions of your plugin. If the script doesn't run, you may have an issue with the `piklist_active_plugin_versions` setting:

* Backup your database
* Note which version of Piklist you are currently running.
* Deactivate and delete Piklist
* Open your database. In the `wp_options` table, look for this field: `piklist_active_plugin_versions` and delete it.
* Reinstall the same version of Piklist you had before. You can download older versions of Piklist from the [bottom of this screen](https://wordpress.org/plugins/piklist/advanced/). 
* The `piklist_active_plugin_versions` should come back to your db.
* Log back into WordPress.
* Upgrade Piklist to the latest version.
* The update script should run.
