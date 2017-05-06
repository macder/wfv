Validation will trigger either a pass or fail action. Hook into them using standard WordPress `add_action()` and process any logic in a callback.

!!! note
    Actions are named using the alias provided when the instance was created:

    `#!js wfv_create( 'contact_form', $form );`

    `Pass: contact_form`<br>
    `Fail: contact_form_fail`

The `FormComposite` instance is automatically passed into the callback. Ensure that the first parameter is reserved for this.


### Pass

```php
<?php // action hook and callback for validation pass

add_action( 'contact_form', 'contact_form_valid' );
function contact_form_valid( $form ) {
  // form input valid, do something...
}
```

### Fail

```php
<?php // action hook and callback for validation fail

add_action( 'contact_form_fail', 'contact_form_invalid' );
function contact_form_invalid( $form ) {
  // form input NOT valid, do something...
}
```
