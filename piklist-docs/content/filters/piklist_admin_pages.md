---
title: "piklist_admin_pages"
description: "The piklist_admin_pages filter lets you register your custom Admin Pages through Piklist. This gives you access to additional functionality that Piklist offers."
hidden: "true"
---

#### `apply_filters('piklist_admin_pages', array());`

The `piklist_admin_pages` filter lets you register your custom Admin Pages through Piklist. This gives you access to additional functionality that Piklist offers.

To register an Admin Page with Piklist:

* Create a function with your Admin Page parameters.
* Hook it to the `piklist_admin_pages()` filter.

This code goes in your theme's functions.php file or your plugin file.

## Parameters
This filter supports every parameter that [`add_menu_page()`](https://developer.wordpress.org/reference/functions/add_menu_page/) supports. Additionally, you may use the following Piklist specific parameters.

### `menu_title`

Title for the menu

* Input:  string

```
'menu_title' => 'My Page'
```

### capability

What user capability can see this page.

* Input:  string

```
'capability' => 'manage_options'
```

### `section`

### `notice`

### `title`
Page Title

* Input:  string

```
'title' => 'Welcome to our admin page'
```

### sub_menu
Should this page be the sub menu of another page.

* Input: string

```
'sub_menu' => 'options-general.php'
```

```
'sub_menu' => 'my_menu'
```

### `menu_slug`
The url slug of this page.

* Input: string

```
'menu_slug' => 'my_menu_settings'
```

### `setting`
If this page will be used to save settings, specify the setting.

* Input:  string

```
'setting' => 'my_setting'
```

### `page_sections`

### `menu_icon`
URL to an image file for the menu icon

* Input: string (url)

```
'menu_icon' => get_stylesheet_directory_uri() . 'images/my-menu-icon.svg'
```

### `save`
Show the "Save" button or not.

* Input:  boolean

```
'save' => true
 ```

### `save_text`
 Text for the Save button

 * Input:  string
 * Default: Save Changes

 ```
 'save_text' => Save your settings
  ```

### `page`

### `layout`


## EXAMPLE (FROM PIKLIST):
```
add_filter('piklist_admin_pages', 'my_admin_pages');

function my_admin_pages($pages) {

    $pages[] = array(
      'page_title' => __('About', 'piklist')
      ,'menu_title' => __('Piklist', 'piklist')
      ,'capability' => defined('PIKLIST_SETTINGS_CAP') ? PIKLIST_SETTINGS_CAP : 'manage_options'
      ,'menu_slug' => 'piklist'
      ,'single_line' => false
      ,'menu_icon' => piklist::$add_ons['piklist']['url'] . '/parts/img/piklist-menu-icon.svg'
      ,'page_icon' => piklist::$add_ons['piklist']['url'] . '/parts/img/piklist-page-icon-32.png'
    );

    $pages[] = array(
      'page_title' => __('Piklist Settings', 'piklist')
      ,'menu_title' => __('Settings', 'piklist')
      ,'capability' => defined('PIKLIST_SETTINGS_CAP') ? PIKLIST_SETTINGS_CAP : 'manage_options'
      ,'sub_menu' => 'piklist'
      ,'menu_slug' => 'piklist-core-settings'
      ,'setting' => 'piklist_core'
      ,'menu_icon' => piklist::$add_ons['piklist']['url'] . '/parts/img/piklist-menu-icon.svg'
      ,'page_icon' => piklist::$add_ons['piklist']['url'] . '/parts/img/piklist-page-icon-32.png'
      ,'single_line' => true
    );

    $pages[] = array(
      'page_title' => __('Piklist Add-ons', 'piklist')
      ,'menu_title' => __('Add-ons', 'piklist')
      ,'capability' => defined('PIKLIST_SETTINGS_CAP') ? PIKLIST_SETTINGS_CAP : 'manage_options'
      ,'sub_menu' => 'piklist'
      ,'menu_slug' => 'piklist-core-addons'
      ,'setting' => 'piklist_core_addons'
      ,'menu_icon' => piklist::$add_ons['piklist']['url'] . '/parts/img/piklist-menu-icon.svg'
      ,'page_icon' => piklist::$add_ons['piklist']['url'] . '/parts/img/piklist-page-icon-32.png'
      ,'single_line' => true
    );

    return $pages;
  }
  ```
