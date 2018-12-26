---
title: Building a simple Admin Page
description: Piklist makes it super easy to create admin pages in WordPress.
hidden: true
weight: 1
---

## Description
Piklist makes it super easy to create admin pages in WordPress.

{{< show-tutorial-start-folders >}}

* First, we need to register our page with Piklist using the `piklist_admin_pages` filter. This filter adds additional features to the standard WordPress functions [`add_menu_page`](https://developer.wordpress.org/reference/functions/add_menu_page/) and [`add_submenu_page`](https://developer.wordpress.org/reference/functions/add_submenu_page/).

Add this code to your theme's `functions.php` file, or in your custom plugin.

```
add_filter('piklist_admin_pages', 'my_admin_pages');

function my_admin_pages($pages) {

    $pages[] = array(
      'page_title' => 'About this plugin'
      ,'menu_title' => 'About'
      ,'menu_slug' => 'about_my_plugin'
      ,'capability' => 'manage_options'
    );

    return $pages;
  }
```

If you go to the WordPress admin you should see a menu item called "About".


* Now, create a PHP file in your `/parts/admin-pages/` [folder](/folder-structure/). It doesn't matter what you name the file. For this example we'll call it `about.php`.
* At the top of the file, add this code:

```
<?php
/*
 * Page: about_my_plugin
 */
?>
```

This code tells Piklist to place the contents of this file on the `about_my_plugin` page. Notice that the value that goes in `Page:` matches the `menu_slug` you defined when you registered the page.

* NOTE: There are many other [options you can add to the Comment Block](/Piklist-Documentation/folder-structure/comment-block-parameters/).

* Under this comment block you can add text, html, php, etc. Anything you want to show on this page.

For this tutorial, add the following:
```
<p>
    Now is:
    <?php echo date('l jS \of F Y h:i:s A'); ?>
</p>

```

That's it! You just created an Admin Page.

### Full Snippet

```
<?php
/*
 * Page: about_my_plugin
 */
?>
<p>
    Now is:
    <?php echo date('l jS \of F Y h:i:s A'); ?>
</p>

```
