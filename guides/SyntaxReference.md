<img src="https://uploads-ssl.webflow.com/61e714dee6e03a006b829c3a/621cf6cde8ae4f61b08896b4_MORF%20Logo.svg" width="200" height="100" alt="Morf Logo">

# Morf Syntax Reference Guide

## Overview
The Morf form definition is a text document in standard JSON format. The form definiton must be valid JSON for the Morf rendering engine to parse and render the form.  All commas, curly braces, colons and square brackets must be in the correct location. 


The form definiton is in 3 sections: `config`, `head`, and `body`. The `config` section contains configurations that affect the whole form, such as the submission endpoint or theme to style the form. The `head` section describes the form and contains elements such as the title and logo. The `body` section contains the field objects and their properties and may also contain organization elements such as panels. The field objects are within the items array. Objects within a panel must also be in an items array. 

Below is a collapsed view of the form definition:

```
{
    "config": {
          ...
    },
    "head": {
           ...
    },
    "body": {
        "items": [
              ...
        ]
    }
}
```

The tables below describes the valid syntax of the elements of the form definition.

## Config

The config section is the first section in the form description.

| Syntax      | Description | Format |
| ----------- | ----------- | -------- |
| submit     | Location where form data will be submitted via HTTP post.   |   URL       |
| successUrl   | Location where form page will be redirected upon successful submission of form data.        |    URL      |
| sitekey | API authentication key required for form rendering| Unique Key|
| theme  | CSS theme for styling the form.        |     URL of CSS    |
|   externalId     | ID used to identify a form at the author's descretion       |   Alpha numberic ID   |      


## Head

The second section in the form description is the head section.

| Syntax      | Description | Format |
| ----------- | ----------- | -------- |
| title     | Form title, appears centered justified at the top of the form.  |  Text content       |
| logo   | Image to appear in top left corner       |    URL of image file     |


## Body

The final section in the form description is the body section.  Items in the body section are inside the items array.  Each item begins with a `type` which set the type of object and is follow by optional settings which dictate it's behavior.  

### Form Objects

Form objects are defined by their `type` property.  The table below describes the valid types of form objects.

<table>
<tr>
<td> Syntax </td> <td> Description </td> <td> Notes </td> <td> Example </td>
</tr>
<tr>
<td> Button </td>
<td> Displays a button </td>
<td>  </td>
<td>

```json
{
  "type": "button",
  "label": "Button Label"
}
```
</td>
</tr>
<tr><td>checkbox      <td> Displays one or more checkboxes in a group </td><td> Contains an `options` array to list checkboxes in the group. The `options` array is composed of objects with `label` and `value` properties   </td><td>

```json
{
  "type": "checkbox",
  "label": "Select your favorite color(s)",
  "bind": "fav_color",
     "options": [
     {
       "label": "Red",
       "value": "R"
     },
    {
      "label": "Blue",
      "value": "B"
     },
     {
      "label": "Green",
      "value": "G"
     }
  ]
}
```
</td></tr>
<tr><td>color      <td> Displays a color picker  </td><td>    </td><td>

```json
{
   "type": "color",
   "bind": "color_value"
},
```
</td></tr>
<tr><td>date      <td> Displays a date field with date picker  </td><td>  Allows optional text entry  </td><td>

```json
{
  "type": "date",
  "label": "Date",
  "bind" : "date_value"
}
```
</td></tr>
<tr><td>datetimelocal      </td><td> Displays a date and time field with date/time picker  </td><td> Allows optional text entry   </td><td>

```json
{
  "type": "datetimelocal",
  "label": "Date and Time",
  "bind" : "date_time_value"
}
```
</td></tr>
<tr><td>dropdown      <td> Displays a dropdown field with the ability to select an option  </td><td> Contains an `options` array to dropdown values. The `options` array is composed of objects with `label` and `value` properties  </td><td>

```json
{
   "type": "dropdown",
   "label": "What's your favorite color?",
   "bind": "fav_color",
       "options": [
       {
         "label": "Red",
          "value": "R"
       },
       {
         "label": "Blue",
          "value": "B"
       },
       {
          "label": "Green",
          "value": "G"
       }
   ]
},
```
</td></tr>
<tr><td>email      <td> Displays a text field that validates email address format  </td><td>    </td><td>

```json
{
   "type": "email",
   "label": "Contact email",
   "placeholder": "E.g. me@mycompany.com",
   "bind": "contact_email"
}
```
</td></tr>
    <tr><td>file     </td> <td> Displays a file picker object  </td><td>    </td><td>

```json
{
   "type": "file",
   "label": "Attach a file",
   "bind": "attachment"
}
```
</td></tr>
<tr><td>hidden      <td> Creates a hidden fields  </td><td> This object can be used to hold values/variables off screen   </td><td>

```json
{
  "type": "hidden",
  "bind": "hidden_value"
}
```
</td></tr>
<tr><td>month      <td> Displays a month picker  </td><td> Allows optional text entry    </td><td>

```json
{
  "type": "month",
  "label": "Month"
}
```
</td></tr>
<tr><td>number      <td> Displays a field which only allow numberical values  </td><td>    </td><td>

```json
{
  "type": "number",
  "label": "Enter a Number between 1 and 5",
  "minValue": 1,
  "maxValue": 5
}
```
</td></tr>
<tr><td>panel      <td> Display a panel object for grouping objects together   </td><td>    </td><td>

```json
{
   "type": "panel",
    "width": "full",
    "label": "Contact Information",
    "items": [
      {
        "type": "text",
        "label": "Contact Name",
        "placeholder": "E.g. Jane Doe",
        "bind": "name"
      },
      {
        "type": "email",
        "label": "Email",
        "placeholder": "E.g. me@mycompany.com",
        "bind": "email"
      }
    ]
}
```
</td></tr>
<tr><td>password      <td> Displays a field which masks the characters entered  </td><td>    </td><td>

```json
{
   "type": "password",
   "bind": "password"
},
```
</td></tr>
<tr><td>paragraph      <td> Displays a static text paragraph </td><td>    </td><td>

```json
{
   "type": "paragraph",
   "label": "The quick brown fox jumps over the lazy dog",
   "bind": "para_text"
},
```
</td></tr>
<tr><td>radio      <td> Displays one or more radio buttons in a group </td><td>  Contains an `options` array which lists radio buttons in the group. Choices are mutually exclusive. The `options` array is composed of objects with `label` and `value` properties</td><td>

```json
{
   "type": "radio",
   "label": "What's your favorite color?",
   "bind": "fav_color",
       "options": [
       {
         "label": "Red",
          "value": "R"
       },
       {
         "label": "Blue",
          "value": "B"
       },
       {
          "label": "Green",
          "value": "G"
       }
   ]
}
```
</td></tr>
<tr><td>range      <td>Displays a slider for selecting a range  </td><td>    </td><td>

```json
{
   "type": "range",
   "label": "Select Range",
   "bind": "range_value",
   "maxValue": 5,
   "minValue": 1,
   "step": 1
}
```
</td></tr>
<tr><td>reset      <td>Displays a button for clearing form data  </td><td>    </td><td>

```json
{
  "type": "reset",
  "label": "Clear Data"
}
```
</td></tr>
<tr><td>search      <td>Displays a text field with X for clearing value  </td><td>    </td><td>

```json
{
   "type": "search",
   "label": "Search",
   "placeholder": "e.g. The quick brown fox",
   "bind": "search_value"
}
```
</td></tr>
<tr><td>submit      <td>Displays a button which submits the form data  </td><td>  Data is submitted to the URL in the submit element of the `config`  </td><td>

```json
{
  "type": "submit",
  "label": "Submit Form"
}
```
</td></tr>
<tr><td>tel      <td>Displays a text field which formats data according to telephone number pattern </td><td>    </td><td>

```json
{
  "type": "tel",
  "label": "Mobile Number"
}
```
</td></tr>
    <tr><td>text      <td>Displays a text field  </td><td>    </td><td>

```json
{
  "type": "text",
  "placeholder" : "e.g. The quick brown fox jumps over the lazy dog",
  "label": "Text Field Label",
  "bind": "text_field"
}
```
</td></tr>
<tr><td>textarea      <td>Displays a multiline text field  </td><td>    </td><td>

```json
{
   "type": "textarea",
   "label": "Describe the issue",
   "bind": "issue_desc",
},
```
</td></tr>
<tr><td> time     <td>Displays a time picker </td><td>    </td><td>

```json
{
  "type": "time",
  "label": "Time"
}
```
</td></tr>
<tr><td> url     <td>Displays text which can be linked to an URL  </td><td>    </td><td>

```json
{
  "type": "url",
}
```
</td></tr>
    <tr><td> week   </td>  <td>Displays a week picker  </td><td> Allows optional text entry   </td><td>

```json
{
  "type": "week",
  "label": "Week"
}
```
</td></tr>
</table>





### Object Properties

All form objects share a common set of properties which modify their behavior.


  | Syntax      | Description | Notes |
| ----------- | ----------- | -------- |
| ariaLabel     | Provides accessible description of an object | **Note:** Preview only, not a generally available feature. Overrides use of other properties when read by assistive technology.   |
| ariaRole    | Provides accessible role for an object  | **Note:** Preview only, not a generally available feature.   |
| bind     | Provides name and location of where values are written in the JSON data used during submission  | Use a valid JSON dot (`.`) notation to nest bindings within data. Repeatable panels can use the `[*]` to indicate that the number of instances will be dynamically controlled by the form. E.g. `root.repeated[*]` where the child `panel` has `min` and/or `max` properties.    |
| dataType    | Defines the type of data contained in the field. This attribute is used to validate the input | Valid values are `alpha`, `alphaNum`, `numeric`, `integer`, `decimal`, `email`, `url`.   |
| description    | Displays a text description of the field object, can be used for instructions |    |
| disabled     | Specifies if a form object is interactive or read-only  | Valid values are `true` and `false`. Default: `false`.   |
| id     | Used to identify a form object  |   |
| invalidMessage     | A custom validation message to be displayed for invalid fields  |   |
| label     | Displays a label to identify a field  |    |
| mask    | Specifies how data is displayed while a user enters field data  | **Note:** Preview only, not a generally available feature. |
| minLength    | Specifies the minimum length of the entered field value  | Accepts numerical values |
| maxLength    | Specifies the maximum length of the entered field value  | Accepts numerical values |
| minValue    | Specifies the minimum value of the entered field value  | Accepts numerical values |
| maxValue    | Specifies the maximum value of the entered field value  | Accepts numerical values |
| name    | Name of the form object. Will be used as a relative `bind` path if one is not specified | Used to refer to a object in rules and logic.     |
| placeholder    | Specifies text to be displayed in an empty field  | Used to prompt user for appropriate input   |
| regex     | Regular expression  |  Pattern that must be matched for input validation. [Regular expressions](https://en.wikipedia.org/wiki/Regular_expression) follow a standardized format using special characters to denote the pattern. Regular expressions are used by many popular programming languages. **Note:** Slashes (`\`) are escape characters in JSON. To use them in your pattern, make sure to include a double escape e.g. (`\\`)  |
| rules     | Array of event/rule objects that will be bound to the form element  | **Note:** Preview only, not a generally available feature.  |
| required     | Specifies if a form object is required or optional  | Valid values are `true` and `false`. Default: `true` | 
| value   | Data value with which will be used to pre-populated the form element | Valid values are alpha numerical. |
| validation   | Specifies if the default `dataType` field validation should be applied. E.g. `"type": "email"` will automatically validate that the input is a valid email address format.  | Valid values are `true` and `false`. Default: `true` |
| width   | Specifies the screen width the form object should occupy given sufficient space  | Valid values are `full`, `half`, `quarter`, `third`   |


### Panel

The panel object groups other form objects together. Form objects in the panel object are listed in the `items` array much like the `body`.  Panels may be dynamically added or removed.   The min and max properites dictate the minimum and maximum number or times the panel may be repeated.

```
{
    "type": "panel",
    "label": "panel label",
    "name": "mypanel",
    "width": "full",
    "min": 1,
    "max": 3,
    "items": [
        {
            "type": ...
        },
        {
            "type": ...
        },
    ]
}
```


