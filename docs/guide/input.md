## Methods

### **contains()**
Check if the collection contains a key / value pair
~~~{.js}
contains ( $key = null, $value = null )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $key`    | string | `#!js null` | Key
`#!js $value`  | string | `#!js null` | Value to look for
`#!py @return bool`

**Examples**

Basic:
~~~~{.php}
<?php

$input = $form->input();

$input->contains( 'email', 'foo@bar.com');  // true
$input->contains( 'email', 'bar@foo.com');  // false
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

### **display()**
Print an encoded input value to the screen
~~~{.js}
display( $field = null, callable $callback = null )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $field`    | string | `#!js null` |
`#!js $callback`  | callable | `#!js esc_html()` |
`#!py @return string|null`

**Examples**

Basic:
~~~~{.php}
<?php // eg. user entered <h1>Bar</h1>

$form->display('name');

$form->display('input', 'name');

$form->input()->display('name');

$form->display()->input('name');

$form->display()->input('name', 'strip_tags');

$name = $form->encode()->input('name');

$name = $form->escape()->input('name');

~~~~
&lt;h1&gt;Bar&lt;/h1&gt;

!!! note
    The default callback is [esc_html()](https://codex.wordpress.org/Function_Reference/esc_html) when none is provided.

Callback:
~~~~{.php}
<?php // eg. user entered <h1>Bar</h1>

$form->display('name', 'strip_tags'); // Bar
~~~~

!!! tip
    The callable can be a string reference to a function or a closure.

---

### **escape()**
Assign an escaped input value.

~~~{.js}
escape( $key, callable $callback = null )
~~~

Parameter        |  Type  | Default     | Description
--------------   | ------ | ----------- | -----------
`#!js $key`      | string |             | Key containing the string
`#!js $callback` | callable | `#!js esc_html()` | Callback to pass string
`#!py @return string|null`


**Examples**

Basic:
~~~~{.php}
<?php // eg. user entered <h1>Bar</h1>

// no echo
$name = $form->input()->escape('name');  // &lt;h1&gt;Bar&lt;/h1&gt;
~~~~

Callback:
~~~~{.php}
<?php // eg. user entered <h1>Bar</h1>

$name = $form->input()->escape('name', 'strip_tags');  // Bar
~~~~

!!! note
    Make sure to use a callable that is appropriate to the output context.

Custom callback:
~~~~{.php}
<?php // over-engineered string concatenation

function add_lorem( $string ) {
  return $string .'_lorem';
}

$new_name = $form->input()->escape('name', 'add_lorem');

// Bar_lorem
~~~~

Closure:
~~~~{.php}
<?php

$new_name = $form->input()->escape('name', function( $string ){
  return $string .'_lorem';
});

// Bar_lorem
~~~~

Callback with multiple parameters:
~~~~{.php}
<?php // even more over-engineered string concatenation

function wfv_example( $value, $arg2, $arg3 ) {
  return $arg2 .'-'. $value .'-'. $arg3;
}

$callback = array( 'wfv_example', array( 'second', 'third' ) );

$new_email = $form->input()->escape( 'email', $callback );

// second-foo@bar.com-third
~~~~

---

### **has()**
Check if the collection has a given key
~~~{.js}
has ( $key = null )
~~~

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

### **is_populated()**
Checks if the collection has data.
~~~{.js}
is_populated()
~~~

`#!py @return bool`

---
