---
title: "editor Field"
menuTitle: "editor"
---
### `'type' => 'editor'`

Create a standard WordPress editor field.

You can use Piklist field parameters to customize this field.

### Custom Parameters
The editor field takes any option that can be passed to the WordPress [`wp_editor()`](https://codex.wordpress.org/Function_Reference/wp_editor) function. You can pass them through the `options` array. See examples below.

### Examples
**Basic Editor Field**
```
piklist('field', array(
    'type' => 'editor',
    'field' => 'my_editor_field',
    'label' => 'Post Content'
));
```

**Default Editor**

Piklist can replace the default editor in WordPress by using code the following code.
```
piklist('field', array(
    'type' => 'editor',
    'field' => 'post_content', // This is the field name of the WordPress default editor
    'scope' => 'post', // Save to the wp_post table
    'label' => 'Post Content',
    'template' => 'field', // Only display the field not the label
    'options' => array( // Pass any option that is accepted by wp_editor()
      'wpautop' => true,
      'media_buttons' => true,
      'shortcode_buttons' => true,
      'teeny' => false,
      'dfw' => false,
      'quicktags' => true,
      'drag_drop_upload' => true,
      'tinymce' => array(
        'resize' => false,
        'wp_autoresize_on' => true
      )
    )
 ));
```

**Displaying Editor content**

WordPress has a standard function, `the_content()`, for displaying data from the post editor. This function automatically gets filtered by WordPress to format your data correctly. When you want to display data from your custom editor field you may also need to duplicate the functionality of `the_content()``.

Get the field data, and then apply the WordPress filter. Here's an example:
```
$my_field = get_post_meta(get_the_ID(), 'field_name', true);
echo apply_filters( 'the_content', $my_field );
```

Run shortcodes:
Use `do_shortcode()` to run shortcodes in your content.
`echo do_shortcode( get_post_meta( $post->ID, 'field_name', true ) );`

You can even use both together:
```
$my_field = get_post_meta(get_the_ID(), 'field_name', true);
$my_field = apply_filters( 'the_content', $my_field );
echo do_shortcode( $my_field );
```

