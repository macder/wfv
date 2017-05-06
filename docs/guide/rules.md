## Configure

~~~~{.php}
<?php

$rules = array(
  'name' => ['required'],
  'email'=> ['required', 'email'],
)
~~~~


Rule    | Description
------- | ---------------- |
`required` | Required field |
`equals` | Field must equal value from another field (eg. new password confirm) |
`different` | Field value must be different than another field |
`accepted` | Checkbox or Radio must be accepted |
`numeric` | Must be numeric |
`integer` | Must be integer number |
`boolean` | Must be bool |
`array` | Must be array |
`length` | Must be array |
`lengthBetween` | Must be array |
`lengthMin` | Must be array |
`lengthMax` | Must be array |
`min` | Must be array |
`max` | Must be array |
`in` | Must be array |
`ip` | Must be array |
`url` | Must be array |
`urlActive` | Must be array |
`alpha` | Must be array |
`alphaNum` | Must be array |
`slug` | Must be array |
`regex` | Must be array |
`date` | Must be array |
`dateFormat` | Must be array |
`dateBefore` | Must be array |
`dateAfter` | Must be array |
`contains` | Must be array |
`creditCard` | Must be array |
`instanceOf` | Must be array |
`optional` | Must be array |