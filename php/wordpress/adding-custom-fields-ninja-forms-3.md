# Adding a custom field in Ninja Forms 3

Ninja Forms 3 changed the way things works - specifically a custom field is registered - and you now have filters for a lot of stuff.

### So, how do you register a field?

_You'll need PHP 5.4 or newer in order to be able to run the following code. If you're on an older version you can either upgrade or use named functions instead of the anonymous ones_


So here is how you can register a new field:

```
add_filter('ninja_forms_register_fields', function($fields){
  $fields['awesome_custom_field'] = new AwesomeCustomField();

  return $fields;
});
```

_Pay attention to the `awesome_custom_field` key, because is important later on!_

```
class AwesomeCustomField extends NF_Abstracts_Input
{
  function __construct()
  {
    $this->_type = 'awesome_custom_field';
    $this->_name = $this->_type;

    $this->_nicename = __('Our Awesome custom field');
    $this->_section = 'common';
    $this->_icon = 'envelope-o';

    parent::__construct();
  }
}
```

And that's about the minimum needed to create a custom field. Neat, right? :)

But this field doesn't really do anything, so let's add some functionality.

#### Adding custom options to a field

```
class AwesomeCustomField extends NF_Abstracts_Input
{
  public function __construct()
  {
    $this->_type = 'awesome_custom_field';
    $this->_name = $this->_type;

    $this->_nicename = __('Our Awesome custom field');
    $this->_section = 'common';
    $this->_icon = 'envelope-o';

    add_filter('ninja_forms_field_' . $this->_type . '_settings', [$this, 'field_settings']);

    parent::__construct();
  }

  public function field_settings($field_settings)
  {
    $custom_settings = [
      [
        'name' => 'max_value',
        'type' => 'number',
        'label' => __('First option is a number'),

        //for width, you have few options:
        // - full
        // - one-half
        // - one-third
        'width' => 'full',
        'group' => 'primary',
        'value' => 1,
        'help' => __('Here is some help tooltip. Totally optional!'),
      ],

      [
        'name' => 'second_option',

         // Other types includes:
         // - option-repeater
         // - textbox
         // - fieldset
        'type' => 'toggle',
        'label' => __('Second Option'),
        'width' => 'one-third',
        'group' => 'primary',
      ],

      [
        'name' => 'third_option',
        'type' => 'select',
        'options' => [
          [
            'label' => __('First Option'),
            'value' => 1
          ],
          [
            'label' => __('Second Option'),
            'value' => 2
          ]
        ],
        'label' => __('Third Option'),
        'width' => 'full',
        'group' => 'primary',
      ],
    ];

    return array_merge($custom_settings, $field_settings);
  }
}
```

Obviously enough, you could do other stuff, like validation (by adding a `validate` method) or a custom admin element that is visible when you edit a submission (by adding a `admin_form_element` method). You can check all available methods inside of `NF_Abstracts_Field` class.

But what is a custom field that doesn't also have a custom frontend?

#### How to add a custom field frontend?

```
class AwesomeCustomField extends NF_Abstracts_Input
{
  protected $_templates = 'awesome_custom_field';

  public function __construct()
  {
    /..../

    add_filter('ninja_forms_field_template_file_paths', [$this, 'add_custom_template_path']);

    parent::__construct();
  }

  public function add_custom_template_path($templates)
  {
    $templates[] = plugin_dir_path(__FILE__) . '/templates/';

    return $templates;
  }
  /....../
```

You need to add few things on the previous class:

1. a protected `$_templates` variable with the template file name;
2. A filter `ninja_forms_field_template_file_paths` to register a new template directory.
3. Finally, you add the new path. If you're doing this inside of you theme (you shouldn't!), then you will need to use `get_template_directory()` instead of `plugin_dir_path`.

#### Attention!
Your new template file should be named `fields-CUSTOM_TEMPLATE.html`.

Now, your `fields-awesome_custom_field.html` will look something like this:

```
<script id="nf-tmpl-field-awesome_custom_field" type="text/template">
  // your custom field
</script>
```

You can take a look into `includes/Templates/fields-*.html` and see how various fields looks like. However, what we need is a way of displaying custom information.

#### How can we pass data from the PHP to the newly created form element?

Let's add a new filter into the constructor method:

```
add_filter('ninja_forms_localize_field_settings_' . $this->_type, [$this, 'localize_field_settings'], 10, 2);
```

And the new method:

```
  public function localize_field_settings($settings, $form)
  {
     $settings['custom_js_value'] = 'Hello World!';

    return $settings;
  }
```

In our template file, we can simply add the new key:

```
<script id="nf-tmpl-field-awesome_custom_field" type="text/template">
  <%= custom_js_value %>
</script>
```


And that's about all.