---
title: "piklist_pre_update_option"
description: "The piklist_pre_update_option filter is used to filter the settings input before they are saved"
hidden: "true"
---

#### `apply_filters('piklist_pre_update_option', $settings, $setting, $new, $old);`

The piklist_pre_update_option filter is used to filter the settings input before they are saved. This allows you to manipulate the input data, or even add additional settings before the data is entered into the database.

## Parameters
This filter provides you with the following parameters:

### `$settings`

All key=>value pairs for this setting. If you are using multiple tabs, this will show all settings for all tabs.

* Input:  Array

### `$setting`
The name of the setting getting saved.

Input:  Array

### `$new`

This is the data that was entered into the form BEFORE it’s save

* Input:  Array

### `$old`

The data that is in the database

* Input:  Array

Example:

```
 //When the user enters data in the piklist_demo_fields settings page and they press save, add another setting called option_key with the value of option_value.

  add_filter('piklist_pre_update_option','my_update_option', 10, 4);
  function my_update_option($settings, $setting, $new, $old) {

    if ($setting == 'piklist_demo_fields') {
      $settings['option_key'] = 'option_value';
    }

    return $settings;

  }
```
