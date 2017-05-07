## Configure
Override error messages using an array structured like so:
~~~~{.php}
<?php

array(
    'field_name' => array(
        'rule' => 'message'
    ),
);
~~~~

For example, override the `required` error message for the `email` field:
~~~~{.php}
<?php

$messages = array(
  'email' => [
    'required' => 'Your email is required so we can reply back'
  ],
);
~~~~
