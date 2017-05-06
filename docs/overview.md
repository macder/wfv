## What

Working with custom forms in WordPress involves either using some rich WYSIWYG plugin, or writing custom code.

Neither approach is wrong, but sometimes less overhead or no awkward code blocks is more ideal.

Suppose you are creating a custom form and decide to follow the [WordPress way](https://codex.wordpress.org/Plugin_API/Action_Reference/admin_post_%28action%29) as a best practice. You create an action that triggers after a http request to /wp-admin/admin-post.php. So far so good, but that form is posting to `http://yoursite.com/wp-admin/admin-post.php`

Why is this a problem?

The user is no longer on the form. To send them back (i.e a required field was missed), we need to do a HTTP redirect. At this point the `$_POST` with the input is gone... which would have been useful to repopulate the form. In order to persist the users input, it needs to be stored in GET, a session, or a cookie.

Neither is elegant, and both are clunky.

## How
