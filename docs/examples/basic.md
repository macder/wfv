# Basic example

**functions.php**
~~~~{.php}
<?php

$my_form = array(
  'first_name' => [
    'label' => 'First name',
    'rules' => 'required',
  ],
  'email' => [
    'label' => 'Email',
    'rules' => 'required|email',
  ],
);

add_action( 'my_form', 'valid_my_form' );
function valid_my_form( $form ) {
    // Validation passed.
    echo 'Thank you '. $form->input()->escape('first_name');
}

add_action( 'my_form_fail', 'invalid_my_form' );
function invalid_my_form( $form ) {
    // Validation failed.
    // This is mainly for edge cases that require some code after a fail.
    // Most cases will not need this hook.
}

// Turn $my_form into an instance of FormComposite
wfv_create( 'my_form', $my_form );

// Don't believe the magic?
print_r( $my_form );
~~~~

**Theme template**
~~~~{.html}
<form method="post">

  <input name="first_name" type="text" value="<?php $my_form->display('first_name'); ?>">
  <small><?php echo $my_form->errors()->first('first_name'); ?></small>

  <input name="email" type="text" value="<?php $my_form->display('email'); ?>">
  <small><?php echo $my_form->errors()->first('email'); ?></small>

  <?php $my_form->get_token_fields(); ?>
  <input type="submit" value="Send">

</form>
~~~~
