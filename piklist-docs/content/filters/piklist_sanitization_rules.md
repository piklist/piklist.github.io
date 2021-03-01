---
title: "piklist_sanitization_rules"
description: "Add your own rules to sanitize field data."
hidden: "true"
---

#### `apply_filters('piklist_sanitization_rules', self::$sanitization_rules);`

Add your own rules to [sanitize field data](/fields/sanitizing-fields/).

Example:
```
// create a sanitization rule called "my_email_sanitization"

  add_filter('piklist_sanitization_rules', 'sanitize_email_function', 11);
  function sanitize_email_function($sanitization_rules) {
    $sanitization_rules['my_email_sanitization'] = array(
      'callback' => 'sanitize_email_callback'
    );

    return $sanitization_rules;
  }

  function sanitize_email_callback($value, $field, $options) {
    return sanitize_email($value); // sanitize_email() is a core WordPress function
  }
```

Usage:

```
'sanitize' => array(
  array(
    'type' => 'my_email_sanitization'
  )
)
```
