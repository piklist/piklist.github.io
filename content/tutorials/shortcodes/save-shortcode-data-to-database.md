---
title: Save Shortcode data to database
description: Save Shortcode data to database
hidden: true
---

## Description

With Piklist you can save shortcode data to your database instead of the WordPress editor.

{{< show-tutorial-start-folders >}}

In this tutorial we'll save add_more (repeater) data to the database, since this data would be difficult to show in a standard shortcode.

### Create the field
Open or create your shortcodes form file and add this field:

```
piklist('field', array(
    'type' => 'text'
    ,'field' => 'my_shortcode_saved_to_db'
    ,'scope' => 'post_meta'
    ,'save_id' => isset($shortcode['attributes']['my_shortcode_saved_to_db']) ? (int) $shortcode['attributes']['my_shortcode_saved_to_db'] : true // Get the meta_id from the shortcode
    ,'label' => 'Demo shortcode'
    ,'add_more' => true
));
```

A few things about this field:

  * We are setting the `scope` to post_meta, to tell Piklist where to save the data. This can also be user_meta, term_meta, etc.
  * The `save_id` parameter is the meta_id in your database. This line is telling Piklist to retrieve the meta_id.  This is what will be shown in the post editor.


### Save the meta data

Add the following directly under the above field.

```
// Get the last field rendered
$field = piklist('field');

// Store our meta id on the shortcode using the same field name as the post_meta for easy reference. Yes, we know there are two fields in this file with the same name, `my_shortcode_saved_to_db`. Don't worry, it's fine.
piklist('field', array(
  'type' => 'hidden'
  ,'field' => 'my_shortcode_saved_to_db'
  ,'value' => $field['data_id']
));
```

The shortcode itself will render something like `[source_information sources_group="506"]Your text here[/source_information]` in your post. In this example the `506`, is the `meta_id` from the database. Since you can use this shortcode multiple times in one post, this is the only ID that is unique to this row.

If you save this shortcode you should see the `my_shortcode_saved_to_db` field in your database. You can then retrieve it normally.
