Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec tincidunt iaculis ullamcorper.

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