# Morf Editor

## Overview
The Morf Editor is the tool for creating and editing Morf data capture experiences.  The editor can be found at https://editor.getmorf.io/.  The left hand pane of the editor contains the Morf form defintion in JSON format, while the right hand pane contains the form in a live preview mode.  Changes to the JSON form definition are immediately reflected in the live preview.
The form definition must comply with the markup in the Morf [Syntax Reference](SyntaxReference.md).

![image](https://user-images.githubusercontent.com/17143489/187986114-11088f71-d582-4419-afd4-5efb7f95e8a4.png)

## Menu Options
Along the top of the Morf Editor are several menu options to help you create form and control your editor user experience.

### Convert
You can create a Morf form by converting a Microsoft Word document containing [Adobe Document Generation tags](https://developer.adobe.com/document-services/docs/overview/document-generation-api/templatetags/) or a PDF containing valid form fields.  Morf detects these tags and fields and creates the corresponding fields in the Morf JSON syntax.  The bindings to match the Word or PDF are automatically generated.

### Get Form Data
The Get Form Data button generates a JSON data file containing any data entered into the fields of the live preview pane.  This can be useful when creating applications and workflows for processing the form data.

### Get Embed Tag
Getting an Embed Tag generates the code required to integrate your Morf form into a webpage.  You must have a site key in order to generate embed tags.

### Preview
Preview pops up a preview version of the form in a separate window.   You must have a site key in order to access the preview.

### Get API Access
The Get API Access option presents a small form requesting your first name, last name, organization and the domains from which the site key should be accessible.  Requesting a site key kicks off an approval process.  You will be contacted via email when you are issued a site and/or API key. 

### Checkout the Docs
This links to our [documentation](https://github.com/aftialabs/morf-docs)

### Join Us on Slack!
The Morf Slack channel lets you access the Morf Support, Product Management, Marketing and Engineering team as well as other users of Morf.

### More

#### Settings
Settings provides a place for you to save your site and/or API key and enable/disable the Morf product tour and show/hide the Morf UI branding. See the [URL Modifiers](#url-modifiers) section for additional details on controlling some of these parameters via URL query strings.

## URL Modifiers
### brand
Use the `brand` query string in the Morf editor URL to show/hide the Morf UI branding with a value of `true` or `false`.

For example https://editor.getmorf.io/?brand=false will hide the branding while https://editor.getmorf.io/?brand=true will cause the branding to display (the default).

### formRef
Use the `formRef` query string to pass a public URL location where Morf Editor JSON exists. This will allow the Editor to prefetch a form and load it in the Editor for authoring.