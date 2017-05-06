## Methods

### **Contains**
Check if the collection contains a key / value pair

`#!js contains ( $key = null, $value = null )`

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $key`    | string | `#!js null` | Key
`#!js $value`  | string | `#!js null` | Value to look for

`#!py @return bool`

**Examples**

Basic:
~~~~{.php}
<?php

$my_form->input()->contains( 'email', 'foo@bar.com');  // true
$my_form->input()->contains( 'email', 'bar@foo.com');  // false
~~~~

Conditional:
~~~~{.php}
<?php

$input = $form->input();

if ( $input->contains( 'email', 'foo@bar.com') ) {
    // ...do something
}
~~~~

---

### **Has**
Check if the collection has a given key

`#!js has ( $key = null )`

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $key`    | string | `#!js null` | Key to check existence

`#!py @return bool`

**Examples**

Basic:
~~~~{.php}
<?php

$form->input()->has('email');  // true
~~~~

Conditional:
~~~~{.php}
<?php

$input = $form->input();

if ( $input->has('email') ) {
    // ...do something
}
~~~~

---

### **Is Populated**
Checks if the collection has data.

`#!js is_populated()`

`#!py @return bool`

---

### **Render**
Get an escaped value for safe output.

Use this method to output encoded input values, eg. in markup templates

`#!js render( $key, callable $callback = null )`

Parameter        |  Type  | Default     | Description
--------------   | ------ | ----------- | -----------
`#!js $key`      | string |             | Key containing the string
`#!js $callback` | callable | `#!js esc_html()` | Callback to pass string

`#!py @return string|null`

**Examples**

Basic:
~~~~{.php}
<?php // eg. user entered <h1>Bar</h1>

echo $form->input()->render('name');  // &lt;h1&gt;Bar&lt;/h1&gt;
~~~~

Callback:
~~~~{.php}
<?php // eg. user entered <h1>Bar</h1>

echo $form->input()->render('name', 'strip_tags');  // Bar
~~~~

Custom callback:
~~~~{.php}
<?php // over-engineered string concatenation

function add_lorem( $string ) {
  return $string .'_lorem';
}

$new_name = $form->input()->render('name', 'add_lorem');

echo $new_name;  // Bar_lorem
~~~~

Closure:
~~~~{.php}
<?php

$new_name = $form->input()->render('name', function( $string ){
  return $string .'_lorem';
});

echo $new_name;  // Bar_lorem
~~~~

Callback with multiple parameters:
~~~~{.php}
<?php // even more over-engineered string concatenation

function wfv_example( $value, $arg2, $arg3 ) {
  return $arg2 .'-'. $value .'-'. $arg3;
}

$callback = array( 'wfv_example', array( 'second', 'third' ) );

$new_email = $form->input()->render( 'email', $callback );

echo $new_email; // second-foo@bar.com-third

~~~~
