DMP Form Documentation
==================

###  What to expect from this document
  This document will show you how to create, edit and navigate the complexities of the forms we use at Vivint. This includes html, css, javascript, backend, analytics, and how the forms are used in the company.

#### Index

0. Getting Started
  * Form Submission Process
  * Form Naming Convention
0. HTML/DMP
  * Form View Naming Conventions
  * HTML Forms
0. CSS
0. JavaScript
0. Backend
0. Analytics
0. Company

* * *
#### 1. Getting Started

-----
##### 1.2 Form Submission Process

Forms are submitted and saved to a database (action='/form/capture'). Forms with the truthy field values *faasub_send_to_sfdc* or *faasub_send_to_elq* are submitted to SalesForce or Eloqua, respectively. And various forms are being sent directly to Eloqua.

SalesForce is used as our main CMS.
SalesForce can send data to Eloqua.

Eloqua is used for nuture marketing 

*Form Actions*

0. action="/form/capture" *(Main Action)*
0. action="https://s2984.t.eloqua.com/e/f2"
0.
0.

##### 1.2 Form View Naming Conventions
-----

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

##### 1.2 Form Validation 
----

Every form needs to have form validation. Forms are validated two ways:

0.  HTML5 Form Validation
0.  vivintFormManager.js

>  No additional validation should be necessary.

*Invalid Fields*
0.  HTML5 Validation will display messages. Google "HTML5 validation" if you don't know how to use them.
0.  vivintFormManager.js will add a class ".problem" to the invalid input.
0.  vivintFormManager.js will display an error method (this is currently NOT in use).

> Faas == "Forms as a Service"



The following input field names are used (all fields are required):
	1. FaasSubmission[faasub_name_first] or first_name
	  1.1
	2. FaasSubmission[faasub_name_last]  or last_name
		2.1 
	3. FaasSubmission[faasub_phone] or phone
	  3.1 Input length: 10-18 (min-max) (Both min and max are required.)
	4. FaasSubmission[faasub_postal] or postal
	  4.1 Input length: 5-14 (min-max) (Both min and max are required.
	5. FaasSubmission[faasub_email] or email
		5.1
	6. FaasSubmission[faasub_name_full] or full_name

The following *Hidden Field* names are required for Eloqua
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
	11. {{token id=csrf_name}}

The following can be used as a submit button:

data-done-path : 
data-pp-field :


> Don't use inline JavaScript to submit forms;

#### DMP

> Name views that contain individual forms with: "FORM:[custom name]"
> Views that are wrappers and embed other forms: "form:[custom name]"

v_id 97 FORM: Primary Sales -> Is the main form

> Form Messages should be named: form-m:

###### Embedding forms in DMP

ty_path ->
layout ->
action -> 
foid -> 
sfdc ->
elq ->
button -> 
####  2. CSS
CSS classes used in forms:
subtle_form_result -> Used in the main div wrapper
subtle_form_message -> Used for all form messages
subtle_form -> Used with the <form> tag
i_text -> Used with the text/tel/email input fields
faasub_name_first
faasub_name_last
faasub_phone
faasub_postal
faasub_email -> Used for 
submit-text -> Used to format the consent to be contacted text before the submit button
i_submit ->
faasub_send_to_sfdc ->
faasub_send_to_elq ->
faasub_thank_you_url ->
faasub_source_foid ->
faasub_elq_efid ->
faasub_elq_esid ->
faasub_elq_ecid ->
faasub_elq_ecaid ->
faasub_elq_egid ->
faasub_form_action ->

####  3. JavaScript

	subtle_forms.js
	vivintFormManager.js

#### Validating Forms

1.  All forms should be submitted via standard HTML5 practices to be validated. Use Vivint standard regex patterns for validation.
  
> html5 Phone  RegEx = [\d|\.|\s|\-|\+|\(|\)]{10,18}
> html5 postal Regex = [\d|\s|\-\w]{5,14}

2. vivintFormManager.js, a refactored version of subtle_forms.js(depreciated), is used to validate and control all form submission.  vivintFormManager.js is used to pre-populate fields, run validation, show error messages and submit the form. It uses the same regexs as the HTML5 patterns.


####  4. Backend



####  5. Analytics

Analytics are sent to the following:
1. Google Analytics - 
2. Eloqua - Used for nurturing and remarketing ("Faas" prefix is used for Eloqua)
3. SaleForce - 
4. Site Catalyst - 
5. Optimizely - Used for test data and conversion rates

####  6. Company 

