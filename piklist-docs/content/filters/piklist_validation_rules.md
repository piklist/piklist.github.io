---
title: "piklist_validation_rules"
description: "Add your own rules to validate field data."
hidden: "true"
---

#### `apply_filters('piklist_validation_rules', self::$validation_rules);`

Add your own rules to validate field data.

Example:
```
add_filter('piklist_validation_rules', 'check_valid_number', 11);
  function check_valid_number($validation_rules)
  {
    $validation_rules['my_number'] = array(
      'rule' => "/[-+]?[0-9]*[.,]?[0-9]+/"
      ,'message' => __('is not a number')
    );

    return $validation_rules;
  }
```

Usage:

```
'validate' => array(
  array(
    'type' => 'my_number'
  )
)
```

Create a rule with a callback function:

```
// Create a validation rule called "my_file_exists"

  add_filter('piklist_validation_rules', 'check_file_exists', 11);
  function check_file_exists($validation_rules) {
    $validation_rules['my_file_exists'] = array(
      'callback' => 'my_validate_file_exists'
    );

    return $validation_rules;
  }


  /**
   * @param int $index The field index being checked.
   * @param mixed $value The value of the field.
   * @param array $options The options.
   * @param array $field The field object.
   * @param array $fields Collection of fields.
   */
  function my_validate_file_exists($index, $value, $options, $field, $fields) {
    return @file_get_contents($value) ? true : 'contains a file that does not exist.';
  }
```
