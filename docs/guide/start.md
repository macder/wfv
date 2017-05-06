WFV takes in an array of arguments to create the object you will interact with.

This array will contain 2 arrays - rules, and messages

---

### **Define Validation Rules**
The rules array defines the validation rule(s) for each field
~~~~{.php}
<?php

$rules = array(
  'name' => ['required'],
  'email'=> ['required', 'email'],
)
~~~~
Each field holds an array of rules. You can use [built-in](/guide/rules/#built-in-rules) ones or [create your own](/guide/rules/#custom-rules).

---

### **Override Messages**
The messages array overrides an error message for a field's rule
~~~~{.php}
<?php

$messages = array(
  'email' => [
    'required' => 'Your email is required so we can reply back'
  ],
)
~~~~

---

### **Declare**
Define your validation rules and message overrides using this structure:
~~~~{.php}
<?php

$form = array(
  'rules'  => array(
    'name' => ['required'],
    'email'=> ['required', 'email'],
  ),

  'messages' => array(
    'email' => [
      'required' => 'Your email is required so we can reply back'
    ],
  )
);
~~~~

---

### **Activate**
Pass the array of arguments into the [wfv_create()](/guide/create) function to get an instance of `WFV\FormComposite`
