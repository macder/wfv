## Define
Rules are defined in a field's rules attribute in the config array:
~~~
<?php

array(
    'first_name' => [
        'label' => 'First Name',
        'rules' => 'required|max:30'
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
Rules          |                |              |             |
---------------| ---------------|--------------|-------------|
[`#!js alpha`](#alpha)       | [`#!js lorem`](#)       | [`#!js lorem`](#)      | [`#!js lorem`](#)     | [`#!js lorem`](#)  
[`#!js alpha_dash`](#alpha_dash)       | [`#!js lorem`](#)        | [`#!js lorem`](#)      | [`#!js lorem`](#)     | [`#!js lorem`](#)
[`#!js alpha_num`](#alpha_num)        | [`#!js lorem`](#)        | [`#!js lorem`](#)      | [`#!js lorem`](#)     | [`#!js lorem`](#)
[`#!js lorem`](#)        | [`#!js lorem`](#)       | [`#!js lorem`](#)      | [`#!js lorem`](#)     | [`#!js lorem`](#)

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

### **alpha_num_dash**
Input value must only contain alphabetic and numeric characters, dashes, and underscores.

`#!js 'alpha_num_dash'`

---

### **array**

`#!js 'array'`

---

### **between**

`#!js 'between:10,20'`

---

### **boolean**

`#!js 'boolean'`

---

### **callback**

`#!js 'callback:my_function'`

---

### **date**
Input value must be a date.

`#!js 'date'`

---

### **different**

`#!js 'different'`

---

### **digits**

`#!js 'digits'`

---

### **email**
Input value must be formatted like an email address.

`#!js 'email'`

---

### **equals**

`#!js 'equals'`

---

### **integer**

`#!js 'integer'`

---

### **ip**

`#!js 'ip'`

---

### **max**

`#!js 'max:20'`

---

### **min**

`#!js 'min:5'`

---

### **numeric**
Input value must be numeric.

`#!js 'numeric'`

---

### **optional**
The field is optional. Any other defined rules will only be validated if field is not empty.

`#!js 'optional'`

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
