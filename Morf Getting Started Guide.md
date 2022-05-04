# Morf Getting Started Guide

## What is Morf?

Morf is a modern and lightweight API-driven platform that offers a rapid and flexible approach to form and document generation.   Morf enables your organization to overcome the scale of digital transformation by automating the conversion, creation, and maintenance of your forms and documents.  Using Morf, you can quickly create mobile-ready web forms and tie them into your document generation and electronic signature workflows.

## The Morf Difference

Instead of trying create yet another drag and drop form editor, Morf allows you to quickly define you form with a simple declarative syntax.  The editor provides tyep-ahead hints and real-time form preview.  Better yet, Morf converts your existing forms and documents into the form definition and creates the corresponding data bindins. Within mere minutes, you can start collecting data that flows into dynamic signature-ready documents and into any backend system of record.  

## Creating Morf Forms

To create your first Morf form, navigate to https://editor.getmorf.io/.  In the left-hand panel, you can edit the form defintion.   In the right-hand pane you can see a real-time preview of the form.

The definition consists of 3 main parts: 
<ul>
  <li>config</li>
  <li>head</li>
  <li>body</li>  
</ul>

The config section contains configurations that affect the whole form, such as the submission endpoint or theme to style the form.  The head section describes the form and contains elements such as the title and logo.  The body section contains the field objects and their properties and organization elements such as panels.

By default, the editor provides a simple enrollment form. You can try editing and adding to the form to get a feel for Morf.   

Let's add an email field between the last name and the enrollment type.  In the left hand pane insert an open and a closed brace immediately after the comma at the end of the last name object.

    {
      "config": {
        "submit": "",
        "successUrl": "",
        "theme": "",
        "externalId": ""
      },
      "head": {
        "title": "Basic Enrollment Form",
        "logo": "https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg",
          },
      "body": {
        "items": [
          {
            "type": "text",
            "label": "First name",
            "placeholder": "E.g. Jane"
          },
          {
            "type": "text",
            "label": "Last name",
            "placeholder": "E.g. Doe",
            "required": true
          },
          {},
          {
            "type": "radio",
            "label": "Enrollment type",
            "options": [
              {

Between the curly braces enter the word type.  The editor should suggest valid types, select email.   The editor will automatically add quotes and a colon for you.  End the line with a comma.   Now enter the word label and Email Address. Again, end the line with a comma. Enter the word width and the word half. No comma is required after this line.  Your email field object definitioant should not look like this:

        {
          "type": "email",
          "label": "Email Address",
          "width": "half"
        },


It's that easy to build out your form.  Try changing the form title or it's logo.  For more information on the form definition syntax please see the [Morf Syntax Reference Guide](https://github.com/aftialabs/morf-docs/blob/main/Morf%20Syntax%20Reference.md).

## Generating Morf Forms from Documents

