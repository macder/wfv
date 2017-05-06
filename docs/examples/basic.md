# Basic example

`functions.php` or wherever:
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
add_action( 'contact_form', 'my_form_valid' );
function my_form_valid( $form ) {
  // do something...
}

// validation fail
add_action( 'contact_form_fail', 'my_form_invalid' );
function my_form_invalid( $form ) {
  // do something...
}

// create the instance
wfv_create( 'contact_form', $my_form );

// $my_form is now an instance of WFV\Composite\Form:

```

Theme template:
```php
<form method="post">
  <input name="email" type="text">
  <?php $my_form->get_token_fields(); ?>
  <input type="submit" value="Send">
</form>
```