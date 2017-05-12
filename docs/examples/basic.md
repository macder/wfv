# Basic example

`functions.php`
```php
<?php

// declare the rules
$my_form = array(
    'rules' => array(
        'name'  => 'required',
        'email' => 'required|email'
    )
);

function my_form_valid( $form ) {
    echo 'Passed';
}
add_action( 'contact_form', 'my_form_valid' );


function my_form_invalid( $form ) {
    echo 'Failed';
}
add_action( 'contact_form_fail', 'my_form_invalid' );

// create the instance
wfv_create( 'contact_form', $my_form );
```

`some_template.php`
```html
<form method="post">

    <input name="name" type="text"
      value="<?php $my_form->display('name'); ?>">

    <input name="email" type="text">
    <input type="submit" value="Send">

    <?php $my_form->token_fields(); ?>
</form>
```
