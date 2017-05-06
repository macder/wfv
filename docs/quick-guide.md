WFV takes in an array of arguments to create the object you will interact with.

This array will contain 2 arrays - rules, and messages.

Typically, this is defined in a themes `functions.php`, but it can be anywhere.

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
The messages array overrides an error message for a field's rule. This is optional, if no message is provided, the default will be used.
~~~~{.php}
<?php

$messages = array(
  'email' => [
    'required' => 'Your email is required so we can reply back'
  ],
)
~~~~

---

### **Argument Structure**
Define your validation rules and message overrides together in an array structured like this:
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
Pass the array of arguments into the [wfv_create()](/guide/create) function to get an instance of `WFV\FormComposite`.

---

### **Validation Callbacks**

WFV triggers an [action](/guide/hooks) for [pass](/guide/hooks/#pass) or [fail](/guide/hooks/#fail). Hook into them and handle any logic inside callbacks

---

### **Markup a Form**

~~~~.html
<form name="contact_form" method="post">
  <input name="name" type="text">
  <input name="email" type="text">
  <textarea name="msg"></textarea>

  <?php $my_form->get_token_fields(); ?>
  <input type="submit" value="Submit">
</form>
~~~~
