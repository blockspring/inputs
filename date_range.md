# Date Range

Date Ranges aren't a new input type. They are standard date fields with an additional `group` property.

Two consecutive date inputs can have a matching `group` propery used to group the two date inputs together.
The value of the `group` property can be displayed as the name of the combined input.

#### Date Range Example

```json
[
  {
    "name" : "min_date",
    "optional" : false,
    "type" : "date",
    "label" : "Starting Date",
    "help_text" : "Start date for query.",
    "default" : "2015-01-01",
    "group": "Publish Date"
  },
  {
    "name" : "max_date",
    "optional" : false,
    "type" : "date",
    "label" : "End Date",
    "help_text" : "End date for query.",
    "default" : "2015-12-31",
    "group": "Publish Date"
  }
]
```

#### Multiple Date Range Example

```json
[
  {
    "name" : "min_publish_date",
    "optional" : false,
    "type" : "date",
    "label" : "Start Date",
    "help_text" : "Earliest date of publishing.",
    "default" : "2015-01-01",
    "group": "Publish Date"
  },
  {
    "name" : "max_publish_date",
    "optional" : false,
    "type" : "date",
    "label" : "End Date",
    "help_text" : "Latest date of publishing.",
    "default" : "2015-12-31",
    "group": "Publish Date"
  },
  {
    "name" : "min_created_date",
    "optional" : false,
    "type" : "date",
    "label" : "Start Date",
    "help_text" : "Earliest date of creation.",
    "default" : "2015-01-01",
    "group": "Creation Date"
  },
  {
    "name" : "max_created_date",
    "optional" : false,
    "type" : "date",
    "label" : "End Date",
    "help_text" : "Latest date of creation.",
    "default" : "2015-12-31",
    "group": "Creation Date"
  }
]
```
