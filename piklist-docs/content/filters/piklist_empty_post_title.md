---
title: "piklist_empty_post_title"
description: "Let’s you programmatically set the post title when adding a new post (post type)."
hidden: "true"
---

#### `apply_filters('piklist_empty_post_title', $data['post_title'], $post_array);`

Let’s you programmatically set the post title when adding a new post (post type).

Example:

```
// Set the Post Title to "Order #" plus post ID:
  function set_post_title_to_order_number($data, $post_array) {
    if ($post_array['post_type'] == 'MY-POST-TYPE') {
      return 'Order #' . $post_array['ID'];
    } else {
      return $data;
    }
  }
  add_filter('piklist_empty_post_title', 'set_post_title_to_order_number', 10, 2);
```

IMPORTANT: This filter works best when there is no title field for posts. To disable the title field, do not pass "title" to the supports parameter when registering a post type.

IMPORTANT: You may need to resave your permalinks after loading this function. In the WordPress admin, go to Settings > Permalinks and press save.
