# Number Range

Number Ranges aren't a new input type. They are standard number fields with an additional `group` property.

Two consecutive number inputs can have a matching `group` propery used to group the two number inputs together.
The value of the `group` property can be displayed as the name of the combined input.

#### Number Range Example

```json
[
  {
    "name" : "min_age",
    "optional" : false,
    "type" : "number",
    "label" : "Minimum Age",
    "help_text" : "Minimum age of user.",
    "default" : "2015-01-01",
    "group": "Age Range"
  },
  {
    "name" : "max_age",
    "optional" : false,
    "type" : "number",
    "label" : "MAximum Age",
    "help_text" : "Maximum age of user.",
    "default" : "2015-12-31",
    "group": "Age Range"
  }
]
```
