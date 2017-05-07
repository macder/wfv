
### **wfv_create**
This method will pass by reference an instance of `FormComposite` as described by the $array arguments.

You must call this method to actualize a validation. It takes the boring array of arguments and gives you a rich composite.
~~~{.js}
wfv_create( string $action, array &$form )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $action`    | string |    |
`#!js $form`    | array |    |

!!! warning
    When using validation hooks, this method must be called after they have been registered.

    Place `wfv_create()` below the hooks.

~~~~{.php}
<?php
wfv_create( 'contact_form', $form );
~~~~
`$form` is now an instance of `WFV\FormComposite`
