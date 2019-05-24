## Conditions

Set conditions for your fields.

* Input:  parameters
* values:  An array of conditions

### Sub Parameters:

#### relation (sub parameter)
When using multiple conditions, the default logic is AND. Use this parameter to change the logic to OR.
Examples:
`'relation' => 'or'`
`'relation' => 'and'`

#### field (sub parameter)
The name of the field you will be watching for Hide/Show, or the field you will be Updating.
Example:
`'field' => 'my_field'`

#### value (sub parameter)
The value(s) of the field that will trigger the condition. This parameter also accepts an array of values.
Examples:
`'value' => 'yes'`
`'value' => array('yes', 'maybe')`

#### reset (sub parameter)
By default, any field that is hidden/shown will have their values reset. To prevent this set reset to false.
Example:
`'reset' => 'false'`

#### compare (sub parameter)
Operator to test the value against. Currently only two values are supported: == and !=.
* default: ==

Example:
`'compare' => '!='`

#### type (sub parameter)
Piklist supports two condition types; `toggle` and `update`.
* default: toggle

Example:
`'type' => update`

#### scope (sub parameter)
IMPORTANT: Only use if you manually set the scope in the field you are monitoring for Hide/Show.
Example:
`'scope' => taxonomy`

#### post_status_hide (sub parameter)

#### post_status_value (sub parameter)



Example:
```
  // Demonstrates a lot of conditional fields working together


  // Show this field if (guest_meal == steak) or (guest_one_meal == steak) or (guest_two_meal == steak)
  piklist('field', array(
    'type' => 'html'
    ,'field' => '_message_meal'
    ,'value' => __('We only serve steaks rare.', 'piklist-demo')
    ,'attributes' => array(
      'class' => 'piklist-error-text'
    )
    ,'conditions' => array(
      'relation' => 'or'
      ,array(
        'field' => 'guest_meal'
        ,'value' => 'steak'
      )
      ,array(
        'field' => 'guest_one_meal'
        ,'value' => 'steak'
      )
      ,array(
        'field' => 'guest_two_meal'
        ,'value' => 'steak'
      )
    )
  ));

  // Update the field 'guests' to 'yes', if this field is set to ('yes' or 'maybe')
  piklist('field', array(
    'type' => 'select'
    ,'field' => 'attending'
    ,'label' => __('Are you coming to the party?', 'piklist-demo')
    ,'choices' => array(
      '' => ''
      ,'yes' => 'Yes'
      ,'no' => 'No'
      ,'maybe' => 'Maybe'
    )
    ,'conditions' => array(
      array(
        'field' => 'guests'
        ,'value' => array('yes', 'maybe')
        ,'update' => 'yes'
        ,'type' => 'update'
      )
    )
  ));

  // Show this field if the field 'attending' is not eqaual to (empty or 'no')
  piklist('field', array(
    'type' => 'radio'
    ,'field' => 'guest_meal'
    ,'label' => __('Choose meal type', 'piklist-demo')
    ,'choices' => array(
      'chicken' => 'Chicken'
      ,'steak' => 'Steak'
      ,'vegetarian' => 'Vegetarian'
    )
    ,'conditions' => array(
      array(
        'field' => 'attending'
        ,'value' => array('', 'no')
        ,'compare' => '!='
      )
    )
  ));

   // Show this field if the field 'attending' is not eqaual to (empty or 'no')
  piklist('field', array(
    'type' => 'select'
    ,'field' => 'guests'
    ,'label' => __('Are you bringing guests', 'piklist-demo')
    ,'description' => __('Coming to party != (No or empty)', 'piklist-demo')
    ,'choices' => array(
      'yes' => 'Yes'
      ,'no' => 'No'
    )
    ,'conditions' => array(
      array(
        'field' => 'attending'
        ,'value' => array('', 'no')
        ,'compare' => '!='
      )
    )
  ));

  // Show this field if the field 'guests_number' is 3
  piklist('field', array(
    'type' => 'html'
    ,'field' => '_message_guests'
    ,'value' => __('Sorry, only two guests are allowed.', 'piklist-demo')
    ,'attributes' => array(
      'class' => 'piklist-error-text'
    )
    ,'conditions' => array(
      array(
        'field' => 'guests_number'
        ,'value' => '3'
      )
    )
  ));

  // Show this field if the field 'attending' is not equal to (empty or 'no')
  // AND the field 'guests' is 'yes'
  piklist('field', array(
    'type' => 'number'
    ,'field' => 'guests_number'
    ,'label' => __('How many guests?', 'piklist-demo')
    ,'description' => __('Coming to party != (No or empty) AND Guests = Yes', 'piklist-demo')
    ,'value' => 1
    ,'attributes' => array(
      'class' => 'small-text'
      ,'step' => 1
      ,'min' => 0
    )
    ,'conditions' => array(
      array(
        'field' => 'attending'
        ,'value' => array('', 'no')
        ,'compare' => '!='
      )
      ,array(
        'field' => 'guests'
        ,'value' => 'yes'
      )
    )
  ));

   // Show this field if the field 'guests_number' not equals (empty or 0)
   // AND the field 'guests' is 'yes'
   // AND 'attending' is not equal to (empty or 'no')
  piklist('field', array(
    'type' => 'group'
    ,'label' => __('Guest One', 'piklist-demo')
    ,'description' => __('Number of guests != empty', 'piklist-demo')
    ,'fields' => array(
      array(
        'type' => 'text'
        ,'field' => 'guest_one'
        ,'label' => __('Name', 'piklist-demo')
      )
      ,array(
        'type' => 'radio'
        ,'field' => 'guest_one_meal'
        ,'label' => __('Meal choice', 'piklist-demo')
        ,'choices' => array(
          'chicken' => 'Chicken'
          ,'steak' => 'Steak'
          ,'vegetarian' => 'Vegetarian'
        )
      )
    )
    ,'conditions' => array(
      array(
        'field' => 'guests_number'
        ,'value' => array('', '0')
        ,'compare' => '!='
      )
      ,array(
        'field' => 'guests'
        ,'value' => 'yes'
      )
      ,array(
        'field' => 'attending'
        ,'value' => array('', 'no')
        ,'compare' => '!='
      )
    )
  ));

  // Show this field if the field 'guests_number' not equals (empty or 0 or 1)
  // AND 'attending' is not equal to (empty or 'no')
  piklist('field', array(
    'type' => 'group'
    ,'label' => __('Guest Two', 'piklist-demo')
    ,'description' => __('Number of guests != (empty or 1)', 'piklist-demo')
    ,'fields' => array(
      array(
        'type' => 'text'
        ,'field' => 'guest_two'
        ,'label' => __('Name', 'piklist-demo')
      )
      ,array(
        'type' => 'radio'
        ,'field' => 'guest_two_meal'
        ,'label' => __('Meal choice', 'piklist-demo')
        ,'choices' => array(
          'chicken' => 'Chicken'
          ,'steak' => 'Steak'
          ,'vegetarian' => 'Vegetarian'
        )
      )
    )
    ,'conditions' => array(
      array(
        'field' => 'guests_number'
        ,'value' => array('', '0', '1')
        ,'compare' => '!='
      )
      ,array(
        'field' => 'attending'
        ,'value' => array('', 'no')
        ,'compare' => '!='
      )
    )
  ));
```
