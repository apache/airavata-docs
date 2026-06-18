##Advance Application Input Configuration

###Introduction

The Django portal for Apache Airavata middleware is new and caters to a wider range of requirements from Gateways. <br>
    
One major requirement was more flexibility in application inputs. In the previous PGA, inputs were Integer, String, Number and URI. 
User requirements were to have more options when adding these input types to their applications, such as option buttons, Cascading inputs, etc…

In Django in order to advance the input types JSON scripting is used. 
When using JSON scripting, prior the developer/gateway admin need to add the component into Django framework in order for it to work.

###String Input Validations

1. When String Inputs are provided, gateway to be able to
    - Define a minimum and a maximum length
    - Define valid characters (only X, Y, Z and 1)
    - Provide validation messages for users.
    - Ignore spaces between letters.
2. A text consisting X, Y, Z with minimum 10 character length and maximum 200 character length.
```
{
    "editor": {
    "ui-component-id": "textarea-input-editor",
    "config": {
    "rows": 6
    },
    "validations": [
          {
            "type": "min-length",
            "value": 10
          },
          {
            "type": "max-length",
            "value": 200
          },
          {
            "type": "regex",
            "value": "^[XYL\\s]+$",
            "message": "Target sequence may only contain letters X, Y and L."
          }
        ]
      }
    }
```
3. “\\\s” in the value confirms ignoring any spaces in the sequence.

###Input List Validations
####Check Boxes
1. When providing inputs, users may need to provide one or many for a single input.
```
{
    "editor": {
        "ui-component-id": "checkbox-input-editor",
        "config": {
            "options": [
                {
                    "value": "a",
                    "text": "A label"
                },
                {
                    "value": "b",
                    "text": "B label"
                },
                {
                    "value": "c",
                    "text": "C label"
                }
            ]
        }
    }
}
```

####Radio Buttons
1. When users are required to select only one input value this is used. If there are more than 6 to select List-of-Values is a better option.
2. If you need to define a ‘default’ value, add the ‘value’ of that option in the Value field in application input. E.g.: If the default is lunch, then the value ‘lunch’ should be added to the Value field in Application input.
```
{
  "editor": {
    "ui-component-id": "radio-button-input-editor",
    "config": {
      "options": [
        {
          "value": "breakfast",
          "text": "Breakfast"
        },
       {
          "value": "lunch",
          "text": "Lunch"
        },
        {
          "value": "dinner",
          "text": "Dinner"
        }
      ]
    }
  }
}
```

####Lists
1. This is where the list is longer than 6 values. 
2. A list longer than 6 values are too lengthy to display as option buttons. Users can use LOVs ( List of Values) if only a single value to be selected, and checkboxes if multiple values are required. 

###Cascading Inputs
1. Cascading inputs are child inputs based on a prior selection. 
2. E.g.: Show value B if value for A is ‘Pizza’. If the input for A is ‘pizza’ Then display B with its values for user to select.

```
{
    "editor": {
        "dependencies": {
            "show": {
                "OR": [
                    {
                        "A": {
                            "comparison": "equals",
                            "value": "pizza"
                        }
                    },
                    {
                        "C": {
                            "comparison": "equals",
                            "value": "cake"
                        }
                    }
                ]
            }
        }
    }
}
```

3. In above, OR means that B to display if value for A is ‘pizza’ or value for C is ‘cake’. In place of OR can use AND and NOT.
4. To toggle properties on the input field, such as "requiredToAddedToCommandLine", add "showOptions" to the JSON config with a value of "toggle" and the names of properties to toggle:
```
{
    "editor": {
        "dependencies": {
            "show": {
                "OR": [
                    {
                        "A": {
                            "comparison": "equals",
                            "value": "pizza"
                        }
                    },
                    {
                        "C": {
                            "comparison": "equals",
                            "value": "cake"
                        }
                    }
                ]
            },
            "showOptions": {
              "toggle": ["requiredToAddedToCommandLine"]
            }
        }
    }
}
```

###Dependent File Uploads
1. Dependent input is an input that is dependent on certain option selected in a previous field. E.g.: If the option selected is ‘list-of-urls’ then show this field to upload a file.
2. If the selected option is ‘list-of-urls’ then the URI upload should be enabled.
```
{
    "editor": {
        "dependencies": {
            "show": {
                "Select reading options": {
                    "comparison": "equals",
                    "value": "list-urls"
                }
            }
        }
    }
}
```