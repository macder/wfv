### **is_valid()**
Convenience method to check if validation passed

~~~{.js}
is_valid()
~~~

`#!py @return bool`

**Example**

Useful for displaying a general success message in a template
~~~~{.php}
<?php if ( $form->is_valid() ) : ?>
  <p>Success!</p>'
<?php endif; ?>
~~~~

---

### **has_errors()**
Convenience method to check if form has input errors

~~~{.js}
has_errors()
~~~

`#!py @return bool`

This is a shorthand for `$form->errors()->is_populated()`

**Example**

Useful for displaying a general error message in a template
~~~~{.php}
<?php if ( $form->has_errors() ) : ?>
  <p>Whoops, some field(s) are not valid</p>'
<?php endif; ?>
~~~~
