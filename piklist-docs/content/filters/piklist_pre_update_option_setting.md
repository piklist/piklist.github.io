---
title: "piklist_pre_update_option_$setting"
description: "The piklist_pre_update_option_$setting filter is used to filter the settings input before they are saved"
hidden: "true"
---

#### `apply_filters('piklist_pre_update_option_' . $setting, $settings, $new, $old);`

The `piklist_pre_update_option_$setting` filter is used to filter the settings input before they are saved. This allows you to manipulate the input data, or even add additional settings before the data is entered into the database.

## Parameters
This filter provides you with the following parameters:

### `$settings`

All key=>value pairs for this setting. If you are using multiple tabs, this will show all settings for all tabs.

* Input:  Array

### `$new`

This is the data that was entered into the form BEFORE it’s save

* Input:  Array

### `$old`

The data that is in the database

* Input:  Array

Example:

```
 //When the user enters data in the piklist_demo_fields settings page and they press save, add another setting called option_key with the value of option_value.

  add_filter( 'piklist_pre_update_option_piklist_demo_fields','my_update_option', 10, 3 );
  function my_update_option($settings, $new, $old) {

      $settings['option_key'] = 'option_value';

    return $settings;

  }
```
