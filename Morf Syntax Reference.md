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

The tables below describe the valid syntax of the elements of the form definition.

## Config

| Syntax      | Description | Format |
| ----------- | ----------- | -------- |
| submit     | Location where form data will be submitted via HTTP post.   |   URL       |
| successUrl   | Location where form page will be redirected upon successful submission of form data.        |    URL      |
| theme  | CSS theme for styling the form.        |     URL of CSS    |
|   externalId     | ??        |   ??   |      
    

## Head
  
  | Syntax      | Description | Format |
| ----------- | ----------- | -------- |
| title     | Form title, appears centered justified at the top of the form.  |  Text content       |
| logo   | Image to appear in top left conver       |    URL of image file     |


## Body



  | Syntax      | Description | Format |
| ----------- | ----------- | -------- |
| button      |   |    |
| checkbox      |   |    |
| color      |   |    |
| date      |   |    |
| datetimelocal      |   |    |
| email      |   |    |
| file      |   |    |
| hidden      |   |    |
| month      |   |    |
| number      |   |    |
| panel      |   |    |
| password      |   |    |
| radio      |   |    |
| range      |   |    |
| reset      |   |    |
| search      |   |    |
| submit      |   |    |
| tel      |   |    |
| textarea      |   |    |
|  time     |   |    |
|  url     |   |    |
|  week     |   |    |


### Panel

### Type
