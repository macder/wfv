description: WFV is an elegant way to work with custom forms in WordPress.

WFV is an elegant way to work with custom forms in WordPress.

A simple fluid and concise API to manage user input, validation, feedback, and safe output.

[Let's begin](/start/)

---

WFV is intended for developers who prefer creating and managing forms at the code level. This is not a WYSIWYG type plugin and is not targeted for users who are not comfortable writing code.

The idea is to give developers full control over custom forms without the heavy footprint of wysiwyg form builders.

Psst, WFV is so flexible that you could use Advanced Custom Fields to build a form. Don't belive the hype? [check this out](https://github.com/macder/derulski.com/blob/develop/wp/wp-content/themes/derulski/templates/template-contact.php)

!!! note
    Documentation is a work in progress.

!!! attention
    Alpha testing stage. Very low risk of breaking changes.


### Features
* 25 [Built-in rules](/guide/rules/#built-in)
* [Custom rules](guide/rules/#custom)
* [Custom error messages](/guide/messages/)
* [Helper methods for safe output](/guide/input/)
* [Auto populate any type of field](/guide/populate/)
* XSS and CSFR prevention
* Supports multiple forms on same page
* [Validation Hooks](/guide/hooks/) if you need to execute code after pass or fail
* Self POST - no redirects, no GET vars, no sessions, no cookies
* No rendered markup
* Developer freedom
