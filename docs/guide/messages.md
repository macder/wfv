## Override
Custom error messages are defined in a field's messages attribute in the config array:
~~~
<?php

array(
    'first_name' => [
        'label' => 'First Name',
        'rules' => 'required',
        'messages' => [
            'required'    => 'Your first name cannot be empty',
        ],
    ]
);
~~~
