---
title: "piklist_part_process"
description: "The `piklist_part_process` filter is used to filter the parts (e.g. meta-boxes, settings, etc.) before they are saved. This allows you to modify or remove parts before they’re processed."
hidden: "true"
---

#### `apply_filters('piklist_part_process', $_part, $folder);`

The `piklist_part_process` filter is used to filter the parts (e.g. meta-boxes, settings, etc.) before they are saved. This allows you to modify or remove parts before they’re processed.

## Parameters

### `$part`

The individual part (e.g. meta-box, setting, etc.) to be modified or removed. It’s an associative array that contains all the information about the part.

* Input:  Array

### `$folder`

The folder the part is stored in. If it’s a meta-box, then this would be “meta-boxes”.

* Input:  Array

Example:

Let’s say we have a couple meta-boxes on our default post type. One of the meta-boxes has a field that asks whether this post is about a magician. We then want another meta-box with details about the magician to only show up if it is. To get the details meta-box to only show up in this instance would look like this:

```
add_filter('piklist_part_process', function($part) {
  global $post;
  // Make sure this is a post edit screen
  if ( $post && 'post' === $post->post_type )
  {
    // Check that this is the right folder and part
    if ( 'meta-boxes' === $folder && 'magician-details.php' === $part['part'] )
    {
      if ( 'yes' !== get_post_meta($post->ID, 'is_magician', true) )
      {
        return false;
      }
    }
  }

  return $part;
 }
```
