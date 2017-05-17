

WFV takes an array of arguments that define the rules and error messages for each field in a form.

Typically, this is defined in a themes `functions.php`, but it can be anywhere.

This array is then passed into `wfv_create( 'my_form', $form_array )` which creates an instance of `FormComposite`.

The `FormComposite` encapsulates all the parts and features of the API. It will do a lot of work for you :)

---

### **Config Structure**

Basic example:
~~~~{.php}
<?php

$my_form = array(
    'first_name' => [
        'label' => 'First Name',
        'rules' => 'required'
    ],
    'last_name' => [
        'label' => 'Last Name',
        'rules' => 'required'
    ],
);
~~~~

---

### **Validation Rules**
The [rules](/guide/rules/) attribute defines the constraint(s) for a field.

You can define multiple rules for a single field by separating each field with a pipe character.
~~~~{.php}
<?php

$my_form = array(
    'first_name' => [
        'label' => 'First Name',
        'rules' => 'required|alpha_dash|max:30'
    ],
    'email' => [
        'label' => 'Email',
        'rules' => 'required|email'
    ],
);
~~~~
You can use [built-in](/guide/rules/#built-in-rules) ones and [create your own](/guide/rules/#custom-rules).

---

### **Error Messages**
Each rule has a default error message, but you may override them with custom ones.
~~~~{.php}
<?php

$my_form = array(
    'first_name' => [
        'label' => 'First Name',
        'rules' => 'required|alpha_dash|max:30',
        'messages' => [
            'required'      => 'Please enter your first name',
            'alpha_dash'    => 'First name can only contain alphabetic characters, dashes, and underscores',
        ]
    ]
);
~~~~
More details about [error messages]().

---

### **Activate**
Pass the array of arguments into the [wfv_create()](/guide/create) function to get an instance of `WFV\FormComposite`.

This will magically turn that boring array into a rich composite object.

Example:
~~~~{.php}
<?php

$form = array( $rules, $messages );
wfv_create( 'my_form', $my_form );

// $my_form is now an instance of FormComposite

$my_form->input()->contains('email', 'foo@bar.com');  // false
$my_form->input()->is_populated(); // false
$my_form->display('email');
// ...
~~~~

!!! note
    The instance is passed by reference to the array of arguments. You do not need to assign it to a variable.

    `$my_form` becomes an instance of FormComposite:
    ~~~
    wfv_create( 'form_name', array $my_form )
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
