---
title: "group Field"
menuTitle: "group"
---
### `'type' => 'group'`

Adds a group of fields.

{{% notice tip %}}
If the main `field` parameter is set, a serialized array is created of all the fields in the group. Not including it saves all the fields as individual meta. Individual meta can easily be searched.
{{% /notice %}}

{{% notice tip %}}
The `columns` field parameter is especially helpful in Field Groups for more complex layouts like address blocks.
{{% /notice %}}

### Examples
```php
piklist('field', array(
    'type' => 'group'
    ,'field' => 'address_group' // removing this parameter saves all fields as separate meta
    ,'label' => __('Address (Grouped)', 'piklist-demo')
    ,'list' => false
    ,'description' => __('A grouped field with the field parameter set.', 'piklist-demo')
    ,'fields' => array(
      array(
        'type' => 'text'
        ,'field' => 'address_1'
        ,'label' => __('Street Address', 'piklist-demo')
        ,'required' => true
        ,'columns' => 12
        ,'attributes' => array(
          'placeholder' => 'Street Address'
        )
      )
      ,array(
        'type' => 'text'
        ,'field' => 'address_2'
        ,'label' => __('PO Box, Suite, etc.', 'piklist-demo')
        ,'columns' => 12
        ,'attributes' => array(
          'placeholder' => 'PO Box, Suite, etc.'
        )
      )
      ,array(
        'type' => 'text'
        ,'field' => 'city'
        ,'label' => __('City', 'piklist-demo')
        ,'columns' => 5
        ,'attributes' => array(
          'placeholder' => 'City'
        )
      )
      ,array(
        'type' => 'select'
        ,'field' => 'state'
        ,'label' => __('State', 'piklist-demo')
        ,'columns' => 4
        ,'choices' => piklist_demo_get_states()
      )
      ,array(
        'type' => 'text'
        ,'field' => 'postal_code'
        ,'label' => __('Postal Code', 'piklist-demo')
        ,'columns' => 3
        ,'attributes' => array(
          'placeholder' => 'Postal Code'
        )
      )
    )
  ));
```

### Usage
#### Display Grouped Fields
If the main `field` value is set for the group, unserialize the contents of the field like this:
```
$group_data = get_post_meta($post->ID, 'address_group', true);
$group_data = maybe_unserialize($group_data); // nice WP helper function to unserialize if needed
print_r($group_data); // output the results or loop through them with a `foreach` statement.
  ```

If the main `field` value is not set for the group, then each field is saved as separate meta. You can retrieve like this:

```
echo get_post_meta($post->ID, 'address_1', false);
echo get_post_meta($post->ID, 'address_2', false);
echo get_post_meta($post->ID, 'city', false);
echo get_post_meta($post->ID, 'state', false);
echo get_post_meta($post->ID, 'postal_code', false);
```