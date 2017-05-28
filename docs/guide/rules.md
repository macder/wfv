## Define
Rules are defined in a field's rules attribute in the config array:
~~~
<?php

array(
    'first_name' => [
        'label' => 'First Name',
        'rules' => 'required|alpha_dash'
    ]
);
~~~

The `field_name` corresponds to the `name` attribute of a field:
~~~~{.html}
<input name="first_name" type="text">
~~~~

---

## Optional Fields
Unless a field is specified as optional, it must pass all the defined validation rules.

For example, in this config, an empty email field would NOT be a valid email and would fail validation:
~~~
<?php

array(
    'email' => [
        'label' => 'Email',
        'rules' => 'email'
    ]
);
~~~

To make the field optional, so that it validates when empty, add the `optional` rule:
~~~
<?php

array(
    'email' => [
        'label' => 'Email',
        'rules' => 'optional|email'
    ]
);
~~~
In this case, validation will only verify the rules for the field if it is not empty.

---

## Built-in


### **alpha**
Input value must only contain alphabetic characters.

`#!js 'alpha'`

---

### **alpha_dash**
Input value must only contain alphabetic characters, dashes, and underscores.

`#!js 'alpha_dash'`

---

### **alpha_num**
Input value must only contain alphabetic and numeric characters.

`#!js 'alpha_num'`

---

### **array_type**
Input value must be a PHP array.

`#!js 'array_type'`

---

### **between**
Input value must be between a range.

Accepted ranges:

* Numeric `#!js 'between:10,20'`
* Alphabetic `#!js 'between:a,f'`
* Date `#!js 'between:2010-01-01,2017-01-01'`
* strtotime `#!js 'between:yesterday,tomorrow'`

`#!js 'between:<start>,<end>'`

---

### **boolean**
Input value must be a boolean.

Accepted values:

* `true`
* `false`
* `'true'`
* `'false'`
* `0`
* `1`
* `'0'`
* `'1'`
* `'on'`
* `'off'`
* `'yes'`
* `'no'`

`#!js 'boolean'`

---

### **callback**
Validate the input value using a callback.

The callback must return boolean.

`#!js 'callback:some_function'`
~~~~{.php}
<?php

function some_function( $input ) {
    return ( 'whatever' === $input ) ? true : false;
}
~~~~
[More details](/guide/rules/#custom)

---

### **date**
Input value must be a date.

Accepted values:

* valid [strtotime](http://php.net/manual/en/function.strtotime.php)
* `instanceof DateTimeInterface`
* `instanceof DateTime`

`#!js 'date'`

You can also specify a format using [date format characters](http://php.net/manual/en/function.date.php),
eg:`#!js 'date:Y-m-d'`


---

### **different**
Input value must be different than the value of another field.

`#!js 'different:other_field'`

---

### **digit**
Input value must be a [digit](https://en.wikipedia.org/wiki/Numerical_digit)

Accepts only `0` through `9`

`#!js 'digit'`

---

### **email**
Input value must be formatted like an email address.

`#!js 'email'`

---

### **equals**
Input value must be equal to given value.

`#!js 'equals:value'`

---

### **integer**
Input value must be an integer.

Accepts only positive/negative whole numbers.

`#!js 'integer'`

---

### **ip**
Input value must be an IP address.

`#!js 'ip'`

---

### **length_max**
Input value length must be less than given value

`#!js 'length_max:value'`

---

### **length_min**
Input value length must be greater than given value

`#!js 'length_min:value'`

---

### **max**
Input value must be less than the maximum.

Numeric:
`#!js 'max:20'`

Alphabetic:
`#!js 'max:c'`

Date:
`#!js 'max:2017-06-30'`

---

### **min**
Input value must be greater than the minimum.

Numeric:
`#!js 'min:20'`

Alphabetic:
`#!js 'min:c'`

Date:
`#!js 'min:2017-06-30'`

---

### **numeric**
Input value must be numeric.

Accepts whole, decimal, positive, and negative numbers

`#!js 'numeric'`

---

### **optional**
The field is optional. All rules for the field will only be validated if field is not empty.

`#!js 'optional'`

---

### **phone**
Input value must be formatted as a phone number.

Valid formats:

* `(555)555-5555`
* `555 555 5555`
* `+5(555)555.5555`
* `33(1)22 22 22 22`
* `+33(1)22 22 22 22`
* `+33(020)7777 7777`
* `03-6106666`

`#!js 'phone'`

---

### **required**
The field is required and must not be empty.

`#!js 'required'`

---

### **required_if**
The field is required only if another field has a specific value.

`#!js 'required_if:other_field,value'`

---

### **required_with**
The field is required only if another field is not empty.

`#!js 'required_with:other_field'`

---

### **same**
Input value must be the same as the value of another field.

This is useful for password and email confirmation fields.

`#!js 'same:other_field'`

---

### **url**
Input value must be formatted as a url.

`#!js 'url'`

---

## Custom
Custom rules can be defined and validated with a callback function.

**Define:**
~~~~{.php}
<?php

$my_form = array(
    'phone' => [
        'label' => 'Phone',
        'rules' => 'required|callback:wfv__phone'
    ],
);
~~~~

**Callback:**

Create a callback that evaluates to true or false:
~~~~{.php}
<?php
// phone field will validate only if the input is 'hi' ...how cruel

function wfv__phone( $value ) {
    return ( 'hi' === $value ) ? true : false;
}
~~~~

!!! note
    To prevent name collisions, it is advised to prefix the function name and/or wrap the function in a `function_exists()` conditional.
