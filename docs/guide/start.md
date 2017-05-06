WFV takes in an array of arguments to create the object you will interact with.

~~~~{.php}
<?php

$rules = array(
  'name' => ['required'],
  'email'=> ['required', 'email'],
)
~~~~

Override default feedback messages:
~~~~{.php}
<?php

$messages = array(
  'email' => [
    'required' => 'Your email is required so we can reply back'
  ],
)
~~~~

Put it together inside an array:
~~~~{.php}
<?php

$form = array(
  $rules,
  $messages
);
~~~~

Activate
~~~~{.php}
<?php
wfv_create( 'contact_form', $form );
~~~~





~~~~{.php}
<?php

~~~~