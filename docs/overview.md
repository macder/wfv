## What

Working with custom forms in WordPress involves either using some rich WYSIWYG plugin, or writing custom code.

Neither approach is wrong, but sometimes less overhead or no awkward code blocks is more ideal.

Suppose you are creating a custom form and decide to follow the [WordPress way](https://codex.wordpress.org/Plugin_API/Action_Reference/admin_post_%28action%29) as a best practice. You create an action that triggers after a http request to /wp-admin/admin-post.php. So far so good, but that form is posting to `http://yoursite.com/wp-admin/admin-post.php`

Why is this a problem?

After submitting, the user is no longer on the form. To send them back (i.e a required field was missed), we need to do a HTTP redirect. At this point the `$_POST` with the input is gone... which would have been useful to repopulate the form. In order to persist that input, it needs to be stored in `GET`, or in the browser as a session or cookie.

Neither is elegant, and both are clunky.

## How

WFV gives you the ability to declare form validation constraints in way that is similar to many MVC frameworks.

Markup a form in a template and define its constraints in functions.php or a plugin.

You get a simple but powerful API that makes coding forms more pleasant.

---

## WFV is:

**Safe:**<br>
~~~{.js}
$form->input()->render('email');
~~~

**Adaptable:**<br>
~~~{.js}
$form->input()->render('email', 'strip_tags')
~~~

**Flexible:**<br>
~~~{.js}
$form->input()->render('email', function( $input ) {
  return strip_tags( $input );
});
~~~

**Aware:**<br>
~~~{.js}
$form->input()->contains( 'email', 'foo@bar.com' );
~~~

**Helpful:**<br>
~~~{.js}
$form->errors->first('email');
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

Enjoy.
