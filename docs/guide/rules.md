## Configure
Rules are defined using an array structured like so:
~~~
<?php

array(
    'field_name' => ['rule', 'rule']
);
~~~

The `field_name` corresponds to the `name` attribute of a field:
~~~~{.html}
<input name="name" type="text">
<input name="email" type="text">
~~~~

Example:
~~~~{.php}
<?php

$rules = array(
    'name' => ['required'],
    'email'=> ['required', 'email'],
)
~~~~

## Built-in Rules
Rule            | Description       
--------------- | ----------------
`required`      | Required field
`equals`        | Field must equal value from another field (eg. new password confirm)
`different`     | Field value must be different than another field
`accepted`      | Checkbox or Radio must be accepted
`numeric`       | Must be numeric
`integer`       | Must be integer number
`boolean`       | Must be bool
`array`         | Must be array
`length`        | Character count must equal given length
`lengthBetween` | Character count must be within given lengths
`lengthMin`     | Character count must be greater
`lengthMax`     | Character count must be less
`min`           | Minimum
`max`           | Maximum
`in`            | Performs in_array check on given array values
`ip`            | Valip IP address
`url`           | Valid URL
`urlActive`     | Valid URL with active DNS record
`alpha`         | Only alphabetic characters
`alphaNum`      | Only alphabetic and numeric characters
`slug`          | URL slug characters (a-z, 0-9, -, _ )
`regex`         | Must match given regular expression pattern
`date`          | Valid date
`dateFormat`    | Valid date in the given format
`dateBefore`    | Valid date before given date
`dateAfter`     | Valid date after given date
`contains`      | Field is a string that contains given string
`creditCard`    | Valid credit card number
`instanceOf`    | Instance of given class
`optional`      | Value does not need to be included in data array. If it is however, it must pass validation

## Custom Rules
Custom rules can be defined and validated with a callback function.

**Define:**
~~~~{.php}
<?php

$rules = array(
  'phone' => ['required', 'custom:phone'],
);
~~~~

**Callback:**

!!! note
    Callback function names must start with `wfv__` followed by the rule name<br>

    This is to prevent naming collisions.

Create a callback that evaluates to true or false:
~~~~{.php}
<?php
// phone field will validate only if the input is 'hi' ...how cruel

function wfv__phone( $value ) {
  return ( 'hi' === $value ) ? true : false;
}
~~~~
