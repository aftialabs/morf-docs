<img src="https://uploads-ssl.webflow.com/61e714dee6e03a006b829c3a/621cf6cde8ae4f61b08896b4_MORF%20Logo.svg" width="200" height="100" alt="Morf Logo">

# Morf Syntax Reference Guide

## Overview
The Morf form definition is a text document in standard JSON format. The form definiton must be valid JSON for the Morf rendering engine to parse and render the form.  All commas, curly braces, colons and square brackets must be in the right place. 


The definiton is in 3 sections: config, head, and body.
The config section contains configurations that affect the whole form, such as the submission endpoint or theme to style the form. The head section describes the form and contains elements such as the title and logo. The body section contains the field objects and their properties and may also contain organization elements such as panels.  The field objects are with the items array.  Objects in a panel must also be in an array. 

Below is a collapsed view of the form definition.

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
              }
            ]
          }
        }

The tables below describes the valid syntax of the elements of the form definition.

## Config

The config section is the first section in the form description.

| Syntax      | Description | Format |
| ----------- | ----------- | -------- |
| submit     | Location where form data will be submitted via HTTP post.   |   URL       |
| successUrl   | Location where form page will be redirected upon successful submission of form data.        |    URL      |
| theme  | CSS theme for styling the form.        |     URL of CSS    |
|   externalId     | ??        |   ??   |      


## Head

The second section in the form description is the head section.

| Syntax      | Description | Format |
| ----------- | ----------- | -------- |
| title     | Form title, appears centered justified at the top of the form.  |  Text content       |
| logo   | Image to appear in top left conver       |    URL of image file     |


## Body

The final section in the form description is the body section.  Items in the body section are inside the items array.  Each item begins with a type which set the type of object and is follow by optional settings which dictate it's behavior.  

The table below describes the valid item types.

  | Syntax      | Description | Notes |
| ----------- | ----------- | -------- |
| button      | Displays a button  |    |
| checkbox      | Displays one or more checkboxes in a group | Contains an options array to list checkboxes in the group   |
| color      | Displays a color picker  |    |
| date      | Displays a date field with date picker  |    |
| datetimelocal      | Displays a date and time field with date/time picker  |    |
| email      | Displays a text field that validates email address format  |    |
| file      | Displays a file picker object  |    |
| hidden      | Createa a hidden fields  | This object can be used to hold values/variables off screen   |
| month      | Displays a month picker  |    |
| number      | Displays a field which only allow numberical values  |    |
| panel      | Display a panel object for grouping objects together   |    |
| password      | Displays a field which masks the characters entered  |    |
| radio      | Displays one or more radio buttons in a group |  Contains an options array which lists radio buttons in the group. Choices are mutually exclusive.  |
| range      | Displays a slider for selecting a range  |    |
| reset      | Displays a button for clearing form data  |    |
| search      | Displays a text field with X for clearing value  |    |
| submit      | Displays a button which submits the form data  |  Data is submitted to the URL in the submit element of the config  |
| tel      |  Displays a text field which formats data according to telephone number pattern |    |
| textarea      | Displays a multiline text field  |    |
|  time     |  Displays a time picker |    |
|  url     | Displays text which can be linked to an URL  |    |
|  week     | Displays a week picker  |    |


### Panel

### Type
