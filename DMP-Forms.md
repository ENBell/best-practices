DMP Form Documentation
==================

###  What to expect from this document
  This document will show you how to create, edit and navigate the complexities of the forms we use at Vivint. This includes html, css, javascript, backend, analytics, and how the forms are used in the company.

#### Index

0. Getting Started
  * Form Submission Process
  * Form Naming Convention
0. HTML
  * Form View Naming Conventions
  * HTML Forms
  * DMP
0. CSS
0. JavaScript
0. Analytics

* * *
#### 1. Getting Started
-----

##### 1.2 Form Submission Process

Forms are submitted and saved to a database (action='/form/capture'). Forms with the truthy field values *faasub_send_to_sfdc* or *faasub_send_to_elq* are submitted to SalesForce or Eloqua, respectively. Various forms are being sent directly to Eloqua.

SalesForce is used as our main CMS.
SalesForce can send data to Eloqua.

Eloqua is used for nuture marketing 

*Form Actions*

0. action="/form/capture" *(Main Action)*
0. action="https://s2984.t.eloqua.com/e/f2"
0.
0.

##### 1.2 Form View Naming Conventions

- FormBase: \[Custom Name\]
> EXAMPLE: FormBase: Primary Sales

- FormBase: \[Custom Name\]\[Modification\]
> EXAMPLE: FormBase: Primary Sales - 3 Form Test

- FormWrap: \[Custom Name\]
> EXAMPLE: FormWrap: Holiday Form

- FormMsg: \[Custom Name\]
> EXAMPLE: FormMsg: Terms and Conditions

- \[Department\]:FormBase: \[Custom Name\]
> EXAMPLE: Solar:FormBase: Primary

- \[Department\]:FormWrap: \[Custom Name\]
> EXAMPLE: Wireless:FormWrap: Special Offer


*Rules For Naming*

1. If you have the form html (<form class="subtle_form {{form_class}}" action="..." ...>) then you are creating a FormBase or a Modification of a Form Base. 
2. If you embed a form view ({{view id=embed v_id=97}}) you are creating a wrapper
3. If you don't embed or use a <form> tag you are creating a FormMsg

*Ideas for Naming:*

1. Time Sensative Forms Need Expirations 
> EXAMPLE: Wireless:FormWrap: BlackFriday (Exp. Dec2014)

* * *
#### 2. HTML
----

##### 2.1 Form Validation 

Every form needs to have form validation. Forms are validated two ways:

0.  HTML5 Form Validation
0.  vivintFormManager.js

>  Additional validation should NOT be necessary.

*Invalid Field Messages*

0.  HTML5 Validation will display messages. Search "HTML5 validation" if you don't know how to use them.
0.  vivintFormManager.js will add a class ".problem" to the invalid input.
0.  vivintFormManager.js will display an error method (this is currently NOT in use).

##### 2.2 Basic From Validation 

Refer to vivintFormManager for all validation requirements.

The following input fields are required:

0. FaasSubmission[faasub_name_full]
1. FaasSubmission[faasub_name_first]
2. FaasSubmission[faasub_name_last]
3. FaasSubmission[faasub_phone]
  * Input length: 10-18 (min-max) (Both min and max are required.)
4. FaasSubmission[faasub_postal] or postal
  * Input length: 5-14 (min-max) (Both min and max are required.
5. FaasSubmission[faasub_email] or email
  * Regex is used to determine if valid address

> Faas == "Forms as a Service"

A few *Hidden Field* used in Eloqua:

1. FaasSubmission[faasub_send_to_sfdc]
2. FaasSubmission[faasub_send_to_elq]
3. FaasSubmission[faasub_thank_you_url]
4. FaasSubmission[faasub_source_foid]
5. FaasSubmission[faasub_elq_efid]
6. FaasSubmission[faasub_elq_esid]
7. FaasSubmission[faasub_elq_ecid]
8. FaasSubmission[faasub_elq_ecaid]
9. FaasSubmission[faasub_elq_egid]
10. FaasSubmission[faasub_form_action]

> Don't use inline JavaScript to submit forms 
*Example*
`html
<a href="javascript:{}" class="button " onclick="document.getElementById('form38').submit();">Submit</a>
`

##### 2.3 DMP

The following form is the primary form in DMP:

> v_id 97 FORM: Primary Sales

###### Embedding forms in DMP

ty_path ->
layout ->
action -> 
foid -> 
sfdc ->
elq ->
button -> 

* * *
####  3. CSS
----

CSS classes used in forms:

- subtle_form_result -> Used in the main div wrapper
- subtle_form_message -> Used for all form messages
- subtle_form -> Used with the <form> tag
- i_text -> Used with the text/tel/email input fields
- faasub_name_first
- faasub_name_last
- faasub_phone
- faasub_postal
- faasub_email -> Used for 
- submit-text -> Used to format the consent to be contacted text before the submit button
- i_submit ->
- faasub_send_to_sfdc ->
- faasub_send_to_elq ->
- faasub_thank_you_url ->
- faasub_source_foid ->
- faasub_elq_efid ->
- faasub_elq_esid ->
- faasub_elq_ecid ->
- faasub_elq_ecaid ->
- faasub_elq_egid ->
- faasub_form_action ->

* * *
####  3. JavaScript
----

##### 3.1 Validating Forms

1. *vivintFormManager.js* a refactored version of subtle_forms.js, is used to validate and control all form submission.  vivintFormManager.js is used to pre-populate fields, run validation, show error messages and submit the form. It uses the same regexs as the HTML5 patterns.

*vivintFormManager.js* is used for all form validation. *vivintFormManager.js* VFM is used on all the 2014 pages. Older pages use the *subtle_forms.js* for validation.

> Don't submit forms using inline javaScript

3. All forms should be submitted via standard HTML5 practices to be validated. Use Vivint standard regex patterns for validation.
  
> html5 Phone  RegEx = [\d|\.|\s|\-|\+|\(|\)]{10,18}
> html5 postal Regex = [\d|\s|\-\w]{5,14}

####  4. Analytics
----

*Forms*
1. SaleForce - 
2. Eloqua - Used for nurturing and remarketing ("Faas" prefix is used for Eloqua)

*Page*
1. Google Analytics - 
2. Site Catalyst - 
3. Optimizely - Used for test data and conversion rates

