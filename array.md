# Array (multiselect)

The `array` type is a new type that is similar to spreadsheet but is only a 1 dimentional array.

Upon receipt of data by our endpoint, any 2D arrays will be converted to a 1D array.

- If the top level array has more than one element, pluck the first element of each second level array.
- If the top level array has only one element, use the only second level array.

__Question:__ The array type __could__ have a subtype of `number` or `text`, do we care?

### NYI: Freeform input type

We have removed the freeform array from the current scope.

### Static list of options

A static list is a precomputed, hardcoded list of options for an input.
This can be configured by setting `options.type = static` and settting an array of options for `options.static`.
Each option is a hash with at least a `value` attribute. With only a `value` attribute, both the value and display name of the option will be the seame. An optional `name` attribute can be used to display a custom name.

#### Static list of options example

```json
{
  "name" : "pets_owned",
  "optional" : false,
  "type" : "array",
  "label" : "Pets Owned",
  "help_text" : "Select all of the pets you own",
  "default" : [],
  "options": {
    "type": "static",
    "static": [
      {
        "name": "Dog",
        "value": "dog"
      },
      {
        "name": "Cat",
        "value": "cat"
      },
      {
        "name": "Dinosaur",
        "value": "impossibro"
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
  "name" : "project_ids",
  "optional" : false,
  "type" : "array",
  "label" : "Project",
  "help_text" : "Projects to search over",
  "default" : [],
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
