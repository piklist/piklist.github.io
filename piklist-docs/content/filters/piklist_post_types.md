---
title: "piklist_post_types"
description: "The piklist_post_types filter lets you register your custom Post Types through Piklist. This gives you access to additional functionality that Piklist offers."
hidden: "true"
---

#### `apply_filters('piklist_post_types', self::$post_types);`

The `piklist_post_type`s filter lets you register your custom Post Types through Piklist. This gives you access to additional functionality that Piklist offers.

To register a Post Type with Piklist:

* Create a function with your Post Type parameters.
* Hook it to the `piklist_post_types()` filter.

This code goes in your theme's functions.php file or your plugin file.

## Parameters
This filter supports every parameter that [`register_post_type()`](http://codex.wordpress.org/Function_Reference/register_post_type) supports. Additionally, you may use the following Piklist specific parameters.

### `admin_body_class`
Add custom classes to the body attribute of any page that displays this post type. In the admin only.

* Input:  Array

```
'admin_body_class' => array(
  'custom-body-class',
  'custom-body-class-2
)
```

### `edit_columns`
Change the titles of the columns on the list posts screen.

* Input:  Array
* values:  array of items to change. key = default WordPress title, value = new title

```
'edit_columns' => array(
  'title' => 'Demo',
  'author' => 'Assigned to'
)
```

### `hide_meta_box`
Easily hide meta boxes per post type. Even if the Post Type "supports" the metabox, you can still hide it

* Input:  Array
* values:  array for metaboxes to hide

```
'hide_meta_box' => array(
  'author'
)
```

### `hide_post_row_actions`
Hide the post row actions that show up when you hover over a post in the list posts screen (e.g. edit, quick edit, trash, preview)

* Input:  Array
* values:  array of row actions, the key corresponding to the span class attribute of the element

```
'hide_post_row_actions' => array(
  'trash',
  'edit',
  'quick-edit'
)
```

### `hide_screen_options`
Hide the screen options tab on the post edit screens.

* Input:  Array

```
'hide_screen_options' => true
```

### `status`
Register custom post statuses to use with this Post Type. A few important notes:
* You must define ALL the statuses for your Post Type.
* Statuses are universal, meaning any status you register cannot have the same key as an existing status. If it does, the label you define will change the other status as well.
* You can use any parameter from the WordPress [`register_post_status`](https://codex.wordpress.org/Function_Reference/register_post_status) function.

* Input:  Array
* values:  array of statuses and labels

```
'status' => array(
  'new' => array(
    'label' => 'New',
    'public' => false
  )
  ,'pending' => array(
    'label' => 'Pending Review',
    'public' => false
  )
  ,'demo' => array(
    'label' => 'Demo',
    'public' => true,
    'exclude_from_search' => true,
    'show_in_admin_all_list' => true,
    'show_in_admin_status_list' => true
  )
  ,'lock' => array(
    'label' => 'Lock',
    'public' => true
  )
)
```

### `title`
Change the “Enter title here” text that appears when you create a new Post.

* Input:  Array
* values:  text you want to show

```
'title' => 'Enter Custom Title'
 ```

NOTE: WordPress doesn’t allow a Post Type slug defined as 'order'. This is not allowed `'slug' => 'order'`

## EXAMPLE:
```
add_filter('piklist_post_types', 'piklist_demo_post_types');

  function piklist_demo_post_types($post_types) {

    $post_types['piklist_demo'] = array(
      'labels' => piklist('post_type_labels', 'Piklist Demo')
      ,'title' => __('Enter a new Demo Title')
      ,'menu_icon' => piklist('url', 'piklist') . '/parts/img/piklist-menu-icon.svg'
      ,'page_icon' => piklist('url', 'piklist') . '/parts/img/piklist-page-icon-32.png'
      ,'supports' => array(
        'title'
        ,'post-formats'
      )
      ,'public' => true
      ,'admin_body_class' => array(
        'custom-body-class'
      )
      ,'has_archive' => true
      ,'rewrite' => array(
        'slug' => 'piklist-demo'
      )
      ,'capability_type' => 'post'
      ,'edit_columns' => array(
        'title' => __('Demo')
        ,'author' => __('Assigned to')
      )
      ,'hide_meta_box' => array(
        'author'
      )
      ,'status' => array(
        'new' => array(
          'label' => 'New'
          ,'public' => false
        )
        ,'pending' => array(
          'label' => 'Pending Review'
          ,'public' => false
        )
        ,'demo' => array(
          'label' => 'Demo'
          ,'public' => true
          ,'exclude_from_search' => true
          ,'show_in_admin_all_list' => true
          ,'show_in_admin_status_list' => true
       )
        ,'lock' => array(
          'label' => 'Lock'
          ,'public' => true
        )
      )
    );
    return $post_types;
  }
  ```
