# Dropdowns

Dropdowns aren't a new input type, rather they are an augmentation of other input types. If you want to lock another input to a limited set of options, add the `options` key to it's configuration.

### Static list of options

A static list is a precomputed, hardcoded list of options for an input.
This can be configured by setting `options.type = static` and settting an array of options for `options.static`.
Each option is a hash with at least a `value` attribute. With only a `value` attribute, both the value and display name of the option will be the seame. An optional `name` attribute can be used to display a custom name.

#### Static list of options example

```json
{
  "name" : "favorite_color",
  "optional" : false,
  "type" : "text",
  "label" : "Favo[u]rite Color",
  "help_text" : "We use your favorite color to determine your life expectancy",
  "default" : "red",
  "options": {
    "type": "static",
    "static": [
      {
        "name": "Red",
        "value": "red"
      },
      {
        "name": "Blue",
        "value": "blue"
      },
      {
        "name": "AMARANTH",
        "value": "dude_thats_a_plant"
      }
    ]
  }
}
```

### TODO: Static option groups


### Dynamic options based on block

Options for an input can also be based on the output of a Blockspring block.

_The `root_key`, `value_key` and `name_key` keys are optional_

_By default, the UI should use the top level array if returned, otherwise use the first non underscored key it finds that contains an array_

_By default, the UI should look for `value` and `name` keys in each object in the array_

__TODO: How do we handle defaults for dynamic?__

```json
{
  "name" : "project_id",
  "optional" : false,
  "type" : "text",
  "label" : "Project",
  "help_text" : "This is the project in your account",
  "default" : "red",
  "options": {
    "type": "block",
    "block": {
      "id": "list-acme-projects",
      "root_key": "projects",
      "value_key": "project_id",
      "name_key": "project_name"
    }
  }
}
```

In the above example, `root_key` defines which root key in the repsonse should be checked for an array of objects. The `name_key` and `value_key` define which attributes of each object in the returned array should be used for the name and value of the options. The following example would be a possible response from the `list-acme-projects` block:

```json
{
  "projects": [
    {
      "project_id": "pr_234j9",
      "owner": "jtokoph",
      "created_at": "2015-09-24",
      "project_name": "Test Project"
    },
    {
      "project_id": "pr_c345",
      "owner": "jtokoph",
      "created_at": "2015-09-03",
      "project_name": "First Project"
    }
  ]
}
```
