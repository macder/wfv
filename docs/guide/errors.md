## Methods

### **has()**
Check if a field has a validation error. This can be useful to display error states.
~~~{.js}
has ( $field = null )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $field`    | string | `#!js null` | Name of the field
`#!py @return bool`

**Examples**

Basic:
~~~~{.php}
<?php

$form->errors()->has('email');
~~~~

Conditional:
~~~~{.html}
<?php
$errors = $form->errors();
?>

<div class="<?php echo ( $errors->has('email') ) ? 'error' : ''">
  <input name="email" type="text">
</div>
~~~~

---

### **first()**
Get the first error message for a given field.

This is useful for displaying inline error messages.
~~~{.js}
first( $field )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $field`  | string |             | Name of the field
`#!py @return string`

**Examples**

Basic:
~~~~{.php}
<?php

echo $form->errors()->first('email');
~~~~

In a template:
~~~~{.html}
<div>
  <input name="email" type="text">
  <small class="error"><?php echo $form->errors()->first('email'); ?></small>
</div>
~~~~
