## Define
Rules are defined using an array structured like so:
~~~
<?php

array(
    'first_name' => 'required|max:100'
);
~~~

The `field_name` corresponds to the `name` attribute of a field:
~~~~{.html}
<input name="first_name" type="text">
<input name="email" type="text">
~~~~

Example:
~~~~{.php}
<?php

$rules = array(
    'first_name' => 'required',
    'email'      => 'required|email',
)
~~~~

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

`#!js 'field' => 'alpha'`

---

### **alpha_dash**
Input value must only contain alpha-numeric characters, dashes, and underscores.

`#!js 'field' => 'alpha_dash'`

---

### **alpha_num**
Input value must only contain alphabetic and numeric characters.

`#!js 'field' => 'alpha_num'`

---

### **array**

`#!js 'field' => ''`

---

### **between**

`#!js 'field' => ''`

---

### **boolean**

`#!js 'field' => ''`

---

### **callback**

`#!js 'field' => ''`

---

### **date**
Input value must be a date.

`#!js 'field' => ''`

---

### **different**

`#!js 'field' => ''`

---

### **digits**

`#!js 'field' => ''`

---

### **email**
Input value must be formatted like an email address.

`#!js 'field' => 'email'`

---

### **equals**

`#!js 'field' => ''`

---

### **integer**

`#!js 'field' => ''`

---

### **ip**

`#!js 'field' => ''`

---

### **max**

`#!js 'field' => ''`

---

### **min**

`#!js 'field' => ''`

---

### **numeric**
Input value must be numeric.

`#!js 'field' => 'numeric'`

---

### **required**
The field is required and must not be empty.

`#!js 'field' => 'required'`

---

### **required_if**
The field is required only if another field has a specific value.

`#!js 'field' => 'required_if:other_field,value'`

---

### **required_with**
The field is required only if another field is not empty.

`#!js 'field' => 'required_with:other_field'`

---

## Custom
Custom rules can be defined and validated with a callback function.

**Define:**
~~~~{.php}
<?php

$rules = array(
    'phone' => 'required|callback:wfv__phone',
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

---
