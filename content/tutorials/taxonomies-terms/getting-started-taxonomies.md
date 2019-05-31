---
title: Getting Started with Taxonomies and Piklist
description: Add some extra power to your Taxonomies by registering them the Piklist way.
hidden: true
weight: 1
---

Whether you register a taxonomy via the standard WordPress function register_taxonomy, or through Piklist, you can still take advantage of many Piklist features. However, you can add some extra power to your Taxonomies by registering them the Piklist way.  Piklist extends the register_taxonomy function with extra parameters to enable extra features.  You can use the standard [`register_taxonomy`](https://codex.wordpress.org/Function_Reference/register_taxonomy) parameters, plus additional ones defined by Piklist.

To register a Taxonomy with Piklist:

* Create a function with your Taxonomy parameters.
* Hook it to the `piklist_taxonomies` filter.
* This code can go in your custom plugin, or your theme’s functions.php file.

```
add_filter('piklist_taxonomies', 'demo_type_tax');
  function demo_type_tax($taxonomies) {
     $taxonomies[] = array(
        'post_type' => 'piklist_demo'
        ,'name' => 'piklist_demo_type'
        ,'show_admin_column' => true
        ,'configuration' => array(
          'hierarchical' => true
          ,'labels' => piklist('taxonomy_labels', 'Demo Type')
          ,'hide_meta_box' => true
          ,'show_ui' => true
          ,'query_var' => true
          ,'rewrite' => array(
            'slug' => 'demo-type'
          )
        )
      );
    return $taxonomies;
  }
 ```
