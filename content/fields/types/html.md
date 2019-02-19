---
title: "html Field"
menuTitle: "html"
---
### `'type' => 'html'`

The Piklist `html` field, allows you to render standard HTML markup and keep the same label/field format as the rest of your fields.

You can use Piklist field parameters to customize this field.

```
piklist('field', array(
    'type' => 'html',
    'label' => 'HTML Field',
    'value' => '<strong>This is some html</strong>',
  ));
```
