## Text Fields

If validation fails, these fields would populate using the submitted values:
```html
<input name="name" type="text" value="<?php $form->display('name'); ?>">
```

```html
<textarea name="msg"><?php $form->display('msg'); ?></textarea>
```

[More options using `display()`](/guide/input/#display)

---

## Checkboxes and Radio
Convenience method to repopulate checkbox input
~~~{.js}
checked_if( string $field, string $value )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $field`    | string | `#!js null` |
`#!js $value`  | string | `#!js null` |
`#!py @return string|null`

Examples:
~~~~{.php}
<?php // will echo 'checked' if user checked 'green' checkbox

echo $form->checked_if('color', 'green'); // checked
~~~~

Checkbox:
~~~~{.html}
<input
  name="color[]"
  type="checkbox"
  value="green"
  <?= $form->checked_if('color', 'green'); ?>
>
~~~~

Radio:
~~~~{.html}
<input
  name="agree"
  type="radio"
  value="yes"
  <?= $form->checked_if('agree', 'yes'); ?>
>
~~~~

---

## Select and Multi-select
Convenience method to repopulate select input
~~~{.js}
selected_if( string $field, string $value )
~~~

Parameter      |  Type  | Default     | Description
-------------- | ------ | ----------- | -----------
`#!js $field`    | string | `#!js null` |
`#!js $value`  | string | `#!js null` |
`#!py @return string|null`

Examples:
~~~~{.php}
<?php // will echo 'selected' if user selected 'green' in select input

echo $my_form->selected_if('color', 'green'); // selected
~~~~

Select:
~~~~{.html}
<select name="title">
  <option value="">Select...</option>
  <option value="Mr" <?= $form->selected_if('title', 'Mr'); ?>>Mr</option>
  <option value="Dr" <?= $form->selected_if('title', 'Dr'); ?>>Dr</option>
  <option value="Miss" <?= $form->selected_if('title', 'Miss'); ?>>Miss</option>
  <option value="Mrs" <?= $form->selected_if('title', 'Mrs'); ?>>Mrs</option>
</select>
~~~~

Multi-select:
~~~~{.html}
<select name="color[]" multiple>
  <option value="red"<?= $form->selected_if('color', 'red'); ?>>Red</option>
  <option value="blue"<?= $form->selected_if('color', 'blue'); ?>>Blue</option>
  <option value="green"<?= $form->selected_if('color', 'green'); ?>>Green</option>
</select>
~~~~
