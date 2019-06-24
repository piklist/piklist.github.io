---
title: Using "Select2" for select fields
description: Select2 is a jQuery replacement for select boxes, and can easily be used with Piklist
hidden: true
---


![Select2 Example](/images/select2.png)


## Description
Piklist makes it easy to create select boxes, but sometimes they can become long with tons of options. Using the ["Select2" jQuery plugin](https://select2.org/) can make them more user-friendly.

* First, let's load two files from Select2. Their javascript and css file. Though the javascript is mandatory, the css is not. You can just borrow from this file if you want.

In your theme's `functions.php` file, or your main plugin file add this code:

```
function my_enqueue_files() {
  wp_enqueue_style( 'select2_styles', 'https://cdnjs.cloudflare.com/ajax/libs/select2/4.0.6-rc.0/css/select2.min.css', false );
  wp_enqueue_script( 'jquery' );
  wp_enqueue_script( 'select2_js', 'https://cdnjs.cloudflare.com/ajax/libs/select2/4.0.6-rc.0/js/select2.min.js', array('jquery'), null, true );
}
add_action( 'wp_enqueue_scripts', 'my_enqueue_files' );
```
Note: for backend (admin) pages like a post editor, use admin_enqueue_scripts action hook instead.

* Now let's add a select field with lots of options. Add this field to the proper file in your `/parts` folder:

```
piklist('field', array(
  'type' => 'select'
  ,'field' => 'us_states'
  ,'label' => 'Select a state'
  ,'required' => true
  ,'choices' => array(
      '' => ''
      ,'AL' => 'AL'
      ,'AK' => 'AK'
      ,'AZ' => 'AZ'
      ,'AR' => 'AR'
      ,'CA' => 'CA'
      ,'CO' => 'CO'
      ,'CT' => 'CT'
      ,'DE' => 'DE'
      ,'DC' => 'DC'
      ,'FL' => 'FL'
      ,'GA' => 'GA'
      ,'HI' => 'HI'
      ,'ID' => 'ID'
      ,'IL' => 'IL'
      ,'IN' => 'IN'
      ,'IA' => 'IA'
      ,'KS' => 'KS'
      ,'KY' => 'KY'
      ,'LA' => 'LA'
      ,'ME' => 'ME'
      ,'MD' => 'MD'
      ,'MA' => 'MA'
      ,'MI' => 'MI'
      ,'MN' => 'MN'
      ,'MS' => 'MS'
      ,'MO' => 'MO'
      ,'MT' => 'MT'
      ,'NE' => 'NE'
      ,'NV' => 'NV'
      ,'NH' => 'NH'
      ,'NJ' => 'NJ'
      ,'NM' => 'NM'
      ,'NY' => 'NY'
      ,'NC' => 'NC'
      ,'ND' => 'ND'
      ,'OH' => 'OH'
      ,'OK' => 'OK'
      ,'OR' => 'OR'
      ,'PA' => 'PA'
      ,'RI' => 'RI'
      ,'SC' => 'SC'
      ,'SD' => 'SD'
      ,'TN' => 'TN'
      ,'TX' => 'TX'
      ,'UT' => 'UT'
      ,'VT' => 'VT'
      ,'VA' => 'VA'
      ,'WA' => 'WA'
      ,'WV' => 'WV'
      ,'WI' => 'WI'
      ,'WY' => 'WY'
  )
  ,'attributes' => array(
    'class' => 'select2-select'
    ,'style' => 'width: 50%'
    ,'data-placeholder' => 'Choose a State'
  )
));
```

Let's take a closer look at this field:

Under `attributes`, we've assigned:

* `'class' => 'select2-select'`: This can be any class you want, but it will allow the Select2 JS to convert this field.
* `'style' => 'width: 50%'`: Setting the width of the field.
* `'data-placeholder' => 'Choose a State'`: Set placeholder text.

Notice we also set the first choice as empty. This is necessary so Select2 can apply the placeholder.

* Last, we need to add some jQuery and pass Select2 options. You can find a full list of options [here](https://select2.org/).

  You can enqueue this code in a separate file, or if you like, you can include it in the same file as your field code:


  ```
  <script>

    jQuery(document).ready(function() {
      jQuery('.select2-select').select2({
          placeholder: "Select a state"
      });
    });

  </script>
  ```

  IMPORTANT: notice that we've included the class `select2-select`, from the field code, in the jQuery script. This tells Select2 which field you want to convert.



### Full Code Snippet:

```
<?php
/*
Title: Select Fields
Post Type: post
*/

piklist('field', array(
  'type' => 'select'
  ,'field' => 'us_states'
  ,'label' => 'Select a state'
  ,'required' => true
  ,'choices' => array(
      '' => ''
      ,'AL' => 'AL'
      ,'AK' => 'AK'
      ,'AZ' => 'AZ'
      ,'AR' => 'AR'
      ,'CA' => 'CA'
      ,'CO' => 'CO'
      ,'CT' => 'CT'
      ,'DE' => 'DE'
      ,'DC' => 'DC'
      ,'FL' => 'FL'
      ,'GA' => 'GA'
      ,'HI' => 'HI'
      ,'ID' => 'ID'
      ,'IL' => 'IL'
      ,'IN' => 'IN'
      ,'IA' => 'IA'
      ,'KS' => 'KS'
      ,'KY' => 'KY'
      ,'LA' => 'LA'
      ,'ME' => 'ME'
      ,'MD' => 'MD'
      ,'MA' => 'MA'
      ,'MI' => 'MI'
      ,'MN' => 'MN'
      ,'MS' => 'MS'
      ,'MO' => 'MO'
      ,'MT' => 'MT'
      ,'NE' => 'NE'
      ,'NV' => 'NV'
      ,'NH' => 'NH'
      ,'NJ' => 'NJ'
      ,'NM' => 'NM'
      ,'NY' => 'NY'
      ,'NC' => 'NC'
      ,'ND' => 'ND'
      ,'OH' => 'OH'
      ,'OK' => 'OK'
      ,'OR' => 'OR'
      ,'PA' => 'PA'
      ,'RI' => 'RI'
      ,'SC' => 'SC'
      ,'SD' => 'SD'
      ,'TN' => 'TN'
      ,'TX' => 'TX'
      ,'UT' => 'UT'
      ,'VT' => 'VT'
      ,'VA' => 'VA'
      ,'WA' => 'WA'
      ,'WV' => 'WV'
      ,'WI' => 'WI'
      ,'WY' => 'WY'
  )
  ,'attributes' => array(
    'class' => 'select2-select'
    ,'style' => 'width: 50%'
    ,'data-placeholder' => 'Choose a State'
  )
));

?>

<script>

  jQuery(document).ready(function() {
    jQuery('.select2-select').select2({
        placeholder: "Select a state"
    });
  });

</script>
```
