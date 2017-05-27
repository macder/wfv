description: A simple, fluid, and concise API to manage user input, validation, feedback, and safe output.

WFV gives you the ability to declare form validation constraints in way that is similar to many MVC frameworks.

Markup a form in a template and define its constraints in functions.php or a plugin.

A simple concrete API that makes coding and validating custom forms in WordPress more pleasant.

---

<!-- ## WFV

**Safe:**<br>
~~~{.js}
$form->escape('email');
~~~

**Adaptable:**<br>
~~~{.js}
$form->display('email', 'strip_tags')
~~~

**Flexible:**<br>
~~~{.js}
$form->escape('email', function( $input ) {
  return strip_tags( $input );
});
~~~

**Aware:**<br>
~~~{.js}
$form->input()->contains( 'email', 'foo@bar.com' );
~~~

**Helpful:**<br>
~~~{.js}
$form->errors()->first('email');
~~~

**Pragmatic:**<br>
~~~{.js}
$form->selected_if('color', 'green');
~~~

**Simple:**<br>
~~~{.js}
$form->input()->has('email');
~~~

**Powerful:**<br>
~~~{.js}
$form->constrain()->validate();
~~~

Enjoy. -->
