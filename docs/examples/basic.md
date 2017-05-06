# Basic example

`functions.php`
```php
<?php

// declare the rules
$my_form = array(
  'rules'   => array(
    'first_name' => ['required'],
    'email'      => ['required', 'email']
  )
);

// validation pass
function my_form_valid( $form ) {
    $name = $form->input()->render('name');
    echo 'Hello '. $name;
}
add_action( 'contact_form', 'my_form_valid' );


// validation fail
function my_form_invalid( $form ) {
    // do something...
}
add_action( 'contact_form_fail', 'my_form_invalid' );

// create the instance
wfv_create( 'contact_form', $my_form );

// $my_form is now an instance of WFV\Composite\Form:

```

`some_template.php`
```html
<form method="post">

    <input name="email" type="text">
    <?php $my_form->token_fields(); ?>
    <input type="submit" value="Send">

</form>
```
