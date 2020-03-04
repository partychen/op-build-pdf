# Reference docs and OPS

This section of the OPS documentation provides APEX partners information on how reference content is published to docs.microsoft.com via OPS. You'll find information in this section on how OPS can provide reference documentation for .NET and Java SDKs, as well as reference documentation for your REST APIs described using Swagger. 

## Onboarding Info

You'll also find information specific to each supported language on how to onboard your reference documentation to the various areas of reference docs centralized on docs.microsoft.com. 

## Currently supported languages

* .NET (C#)
* Java
* REST API 
* PowerShell
* CLI

## Languages Coming this year

* Python (presumed to arrive Spring 2017)

## Unsupported Languages

* Javascript
* C++
* C
* XML Schemas
* F#
* Node.js
* Visual basic
* SOAP API
* OData
* TypeScript

## Supported Git Platforms

Currently only Github is supported for reference content, there is no Appveyor support for VSTS.

## Requirements to Onboard: conceptual vs pure reference

### Conceptual Reference and Supported Languages
If your team has conceptual reference (markdown) and not pure reference (code) for any of the currently supported languages, we *won't be able to onboard you*. Your team needs to bring code for any language supported. For example, if you want to onboard to /dotnet you must have a dotnet binaries.

### Conceptual Reference and *Unsupported* Languages
If your team wants to onboard an unsupported language we could make an exception, we could accept YAML files. If YAML is not an option for your reference content and team, the only other viable alternative would be converting your content to Markdown. 


Example: The UWP team had content in WDCML, but has put in place tooling to convert it to docs-compatible YAML, that allowed them to take advantage of the latest and best reference page template updates. 

 
