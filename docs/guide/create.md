
### **wfv_create**
This method will pass by reference an instance of `FormComposite` as described by the $array arguments.

You must call this method to actualize a validation. It takes the boring array of arguments and gives you a rich composite.
~~~{.js}
wfv_create( string $action, array &$form, bool $trim = true )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $action`    | string |    | Unique identifier for the form
`#!js $form`    | array |    | Configuration array
`#!js $trim`    | bool | true   | Strip whitespace from beginning and end of input values


~~~~{.php}
<?php
wfv_create( 'contact_form', $form );
~~~~
`$form` is now an instance of `WFV\FormComposite`

!!! note
    By default, WFV will trim leading and trailing whitespace from each input value.

    If you do not desire this behavior, pass `false` as a third parameter when calling `wfv_create()`

    eg:
    ~~~~{.php}
    <?php
    wfv_create( 'my_form', $my_form, false );
    ~~~~
