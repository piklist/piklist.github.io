---
title: "datepicker Field"
menuTitle: "datepicker"
---
### `'type' => 'datepicker'`

Create a jQuery datepicker field.

This field uses the standard jQuery DatePicker field, and respects the same options. Just define them in the Piklist options array. See examples below.

You can use Piklist field parameters to customize this field.

**Basic Datepicker field**
```
piklist('field', array(
    'type' => 'datepicker',
    'field' => 'my_date_field',
    'label' => 'Date',
    'value' => date('M d, Y', time() + 604800), // set default value
    'options' => array(
      'dateFormat' => 'M d, yy'
    )
  ));
 ```

 **Localizing the Datepicker field**

The datepicker field can be localized by translating these parameters. This example shows the field being translated into French.

```
piklist( 'field', array(
	'type'    => 'datepicker',
	'field'   => 'my_date_field',
	'label'   => 'Date',
	'options' => array(
		'closeText'          => 'Fermer',
		'prevText'           => 'Précédent',
		'nextText'           => 'Suivant',
		'currentText'        => 'Aujourd\'hui',
		'monthNames'         => [
			'January',
			'February',
			'March',
			'April',
			'May',
			'June',
			'July',
			'August',
			'September',
			'October',
			'November',
			'December',
		],
		'monthNamesShort'    => [
			'Jan.',
			'Feb.',
			'Mar.',
			'Apr.',
			'May.',
			'Jun.',
			'Jul.',
			'Aug.',
			'Sept.',
			'Oct.',
			'Nov.',
			'Dec.',
		],
		'dayNames'           => [ 'Saturday', 'Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday' ],
		'dayNamesShort'      => [ 'Sat.', 'Sun.', 'Mon.', 'Tue.', 'Wed.', 'Thu.', 'Fri.' ],
		'dayNamesMin'        => [ 'S', 'S', 'M', 'T', 'W', 'T', 'F' ],
		'weekHeader'         => 'Sat.',
		'dateFormat'         => 'dd/mm/yy',
		'firstDay'           => 1,
		'isRTL'              => false,
		'showMonthAfterYear' => false,
		'yearSuffix'         => '',
	),
) );
 ```
