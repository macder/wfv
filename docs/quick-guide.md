

WFV takes an array of arguments that define the rules and messages for a form.

Typically, this is defined in a themes `functions.php`, but it can be anywhere.

This array is then passed into `wfv_create( 'my_form', $form_array )` which creates an instance of `FormComposite`.

The `FormComposite` encapsulates all the parts and features of the API. It will do a lot of work for you :)

---

### **Define Validation Rules**
The [rules](/guide/rules/) array defines the validation rule(s) for each field
~~~~{.php}
<?php

$rules = array(
    'name'  => 'required',
    'email' => 'required|email',
);
~~~~
You can use [built-in](/guide/rules/#built-in-rules) ones and [create your own](/guide/rules/#custom-rules).

---

### **Override Messages**
The [messages](/guide/messages/) array overrides an error message for a field's rule. This is optional, if no message is provided, the default will be used.
~~~~{.php}
<?php

$messages = array(
    'email' => [
        'required' => 'Your email is required so we can reply back'
    ],
);
~~~~

---

### **Configuration Array**
[Configure](/guide/configure/) the validation rules, and any message overrides in an array structured like this:
~~~~{.php}
<?php

$form = array(
    'rules'  => array(
        'name' => 'required',
        'email'=> 'required|email',
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

This will magically turn that boring array into a rich composite object.

Example:
~~~~{.php}
<?php

$form = array( $rules, $messages );
wfv_create( 'contact_form', $form );

// $form is now an instance of FormComposite

$form->input()->contains('email', 'foo@bar.com');  // false
$form->input()->is_populated(); // false
$form->display('email');
// ...
~~~~

!!! note
    The instance is passed by reference to the array of arguments.

    ~~~
    wfv_create( 'form_name', array $form )
    ~~~

For available methods, see [input](/guide/input/), [populate](/guide/populate/), and [errors](/guide/errors/)

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

    <?php $form->token_fields(); ?>
    <input type="submit" value="Submit">
</form>
~~~~
