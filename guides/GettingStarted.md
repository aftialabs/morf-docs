<img src="https://uploads-ssl.webflow.com/61e714dee6e03a006b829c3a/621cf6cde8ae4f61b08896b4_MORF%20Logo.svg" width="200" height="100" alt="Morf Logo">

# Morf Getting Started Guide

## What is Morf?

Morf is a modern and lightweight API-driven platform that offers a rapid and flexible approach to form and document generation.   Morf enables your organization to overcome the scale of digital transformation by automating the conversion, creation, and maintenance of your forms and documents.  Using Morf, you can quickly create mobile-ready web forms and tie them into your document generation and electronic signature workflows.

## The Morf Difference

Instead of trying create yet another drag and drop form editor, Morf allows you to quickly define your form with a simple declarative syntax.  The editor provides type-ahead hints and real-time form preview.  Better yet, Morf converts your existing forms and documents into the form definition and creates the corresponding data bindings. Within mere minutes, you can start collecting data that flows into dynamic signature-ready documents and into any backend system of record.  

## Creating Morf Forms

To create your first Morf form, navigate to https://editor.getmorf.io/.  In the left-hand panel, you can edit the form defintion.   In the right-hand pane you can see a real-time preview of the form.

The definition consists of 3 main sections: 
* config
* head
* body 

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
              ...

Between the curly braces enter the word type.  The editor should suggest valid types, select email.   The editor will automatically add quotes and a colon for you.  End the line with a comma.   Now enter the word label and Email Address. Again, end the line with a comma. Enter the word width and the word half. No comma is required after this line.  Your email field object definition should look like this:

        {
          "type": "email",
          "label": "Email Address",
          "width": "half"
        },


It's that easy to build out your form.  Try changing the form title or it's logo.  For more information on the form definition syntax please see the [Morf Syntax Reference Guide](https://github.com/aftialabs/morf-docs/blob/main/Morf%20Syntax%20Reference.md).

## Generating Morf Forms from Documents

Building your form from scratch can be time consuming, but thankfully Morf provides a better way. Organizations looking to accelerate their digital transformation can leverage their existing documents. Morf forms can be machine generated from a document.  This not only creates the field objects but also binds the two so data can easily flow into your document template. When used in conjunction with [Adobe's Document Generation API](https://developer.adobe.com/document-services/apis/doc-generation/) documents are populated with form data.  

### Using Microsoft Word Documents

To indicate where data should appear in your document, simply identify the location with double curly braces `{{ }}` and the name of the field. For example `{{firstname}}`. To nest objects in a data structure, use the dot notation like so `{{vendor.firstname}}`.

To make the tagging process easier, install the [Adobe Document Generation Word Add-in ](https://developer.adobe.com/document-services/docs/overview/document-generation-api/wordaddin/).  The add-in will help you tag the document, create repeating tables and lists, insert calculations and [text tags for Adobe Sign esignatures](https://helpx.adobe.com/sign/using/text-tag.html).

When you are finished tagging your Word document, click on convert in the [Morf editor](https://editor.getmorf.io/) to upload the file. Morf will generate your form.  You'll notice that each field object has an associated "bind" element which matches the double curly brace tags you created.  

**N.B.** Adobe Sign text tags are not converted into field objects.  They become signature fields on the document during the signing process.

### Using PDF Forms

Many organizations use PDF forms that allow the user to fill in Adobe Acrobat Reader and email, or print a document for signature. Adobe Acrobat provides the capability to create these forms by laying form fields on top of an exisitng PDF.   Morf converts the form fields in the PDF into the appropriate Morf form fields.  Field names and binding are determined based on the field names in the PDF.  Labels are based on text near the field. 

Note: XFA-based PDF documents are not yet supported.

## Submitting Data

The data that is captured in your Morf form needs to be submitted to some endpoint.  You can configure this in the submit element at the top of the form definition by entering the URL where you want to post the data. For more information, have a look at our [Submission](./Submission.md) documentation.
## Sample

Wanna try it?  We've put together some [sample assets and a script of instructions](https://github.com/aftialabs/morf-preview/tree/main/demos/education/grantapplication) for you.
This sample will help you build your form from a Word template, populate the Word file with form data and send for signature using Adobe Sign. The process is orchestrated with Microsoft Power Automate.   Enjoy! If you have any issues, contact our [Slack channel](https://getmorf.slack.com/join/signup).
