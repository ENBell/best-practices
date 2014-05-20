DMP Form, Cookie, Tracking Documentation
==================

###  What to expect from this document
  This document will show you how to create, edit and navigate the complexities of the forms we use at Vivint. This includes html, css, javascript, backend, analytics, and how the forms are used in the company.

#### Index

0. Getting Started
  * Form Submission Process
  * Form Naming Convention
  * Ids
  * Cookies
  * Data Fields
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

Forms are submitted and saved to a database (action='/form/capture'). Forms with the truthy field values *faasub_send_to_sfdc* or *faasub_send_to_elq* are submitted to SalesForce or Eloqua, respectively.

SalesForce is used as our main CMS.
SalesForce sends data to Eloqua & Optimizely. 

Eloqua is used for nuture marketing.
Optimizely is used for onpage testing and optimization. 

*Form Actions*

0. action="/form/capture" *(Main Action)*

> By default all forms should be submitted to `/form/capture`

##### 1.2 Form View Naming Conventions

- FormBase: \[Custom Name\]
> EXAMPLE: FormBase: Primary Sales

- FormBase: \[Custom Name\]\[Modification\]
> EXAMPLE: FormBase: Primary Sales - 3 Form Test

- FormWrap: \[Custom Name\]
> EXAMPLE: FormWrap: Holiday Form

- FormItm: \[Custom Name\]
> EXAMPLE: FormItm: Terms and Conditions

- \[Department\]:FormBase: \[Custom Name\]
> EXAMPLE: Solar:FormBase: Primary

- \[Department\]:FormWrap: \[Custom Name\]
> EXAMPLE: Wireless:FormWrap: Special Offer


*Rules For Naming*

1. FormBase: If you have the form html (<form class="subtle_form {{form_class}}" action="..." ...>) then you are creating a FormBase or a Modification of a Form Base. 
2. FormWrap: If you embed a form view ({{view id=embed v_id=97}}) you are creating a wrapper
3. FormItm:  If you don't embed or use a <form> tag you are creating a FormItm

*Ideas for Naming:*

1. Time Sensative Forms Need Expirations 

> EXAMPLE: Wireless:FormWrap: BlackFriday (Exp. Dec2014)

##### 1.3 Ids

Data can be separated into two categories:

1. Tracking Ids
2. Eloqua Ids

*Data Fields Required by SalesForce*

0. EXID => External id - Used to track people brought to vivint site from external campaigns.
0. RMID => Re-Marketing id - Used to track External id people as we continue to remarket.
0. FOID => Form id - Used to track each form variation.
0. OPID => Optimization id - Used for optimization campaigns.
0. CIID => Content Impact - Used to track people brought to vivint site from content writers, bloggers, etc.

Current data is a 4 or 5 digit number piped with at timestamp. Comma separated digit|timestamp pairs may be concatenated.

*Example* `12345|TimeStamp,23456|TimeStamp, ...`

> 4 digit numbers are from older campaigns.

*Depreciated*

0. ATID => All Touch ID -> Used as a history collection all all ids. Each id now keeps a history.
0. SOID => Social ID -> Used to track social campaigns.

##### 1.4 Cookies

Cookies are used to track ids, auto populate forms, and show user(customer, lead, etc) specific data on the page.

*Cookie Keys*

0. VVID
0. atid
0. exid
0. faas
0. faaspre_id
0. foid
0. opid
0. s_cc
0. s_fid
0. s_sq

> Other Cookie key/value pairs do exists.

###### campaigns.js

Defines the following globalDefaultCodes:

```js
var globalDefaultCodes = {
  'exid': {'direct': '28381', 'referral': '28386', 'cookieDays': 90},
  'afid': {'cookieDays': 90},
  'rmid': {'cookieDays': 30},
  'ciid': {'cookieDays': 14},
  'soid': {'cookieDays': 365},
  'opid': {'cookieDays': 0},
  'vendor_id': {'cookieDays': 90},
  'subid': {'cookieDays': 90}
  };
```

##### 1.5 Data Fields

> Taken from the faasSubmission file. Faas == "Forms as a Service"

0. 'faaspre_id' => 'FaaS Pre ID',
0. 'faaspre_faasub_id' => 'FaaS Submission ID',
0. 'faaspre_id' => 'Lead IP',
0. 'faaspre_form_action' => 'Form Action',
0. 'faaspre_email' => 'Email',
0. 'faaspre_name_first' => 'Name First',
0. 'faaspre_name_last' => 'Name Last',
0. 'faaspre_phone' => 'Phone',
0. 'faaspre_postal' => 'Postal',
0. 'faaspre_address_street' => 'Address Street',
0. 'faaspre_address_street2' => 'Address Street2',
0. 'faaspre_city' => 'City',
0. 'faaspre_state' => 'State',
0. 'faaspre_country' => 'Country',
0. 'faaspre_home_owner' => 'Home Owner',
0. 'faaspre_source_hear' => 'Source Hear',
0. 'faaspre_source_exid' => 'Source EXID',
0. 'faaspre_source_rmid' => 'Source RMID',
0. 'faaspre_source_opid' => 'Source OPID',
0. 'faaspre_source_soid' => 'Source SOID',
0. 'faaspre_source_ciid' => 'Source CIID',
0. 'faaspre_source_foid' => 'Source FOID',
0. 'faaspre_source_afid' => 'Source AFID',
0. 'faaspre_source_atid' => 'Source ATID',
0. 'faaspre_send_to_elq' => 'Send to Eloqua',
0. 'faaspre_send_to_sfdc' => 'Send to SFDC',
0. 'faaspre_elq_efid' => 'Eloqua Form Name',
0. 'faaspre_elq_esid' => 'Eloqua Site ID',
0. 'faaspre_elq_ecid' => 'Eloqua Cookie',
0. 'faaspre_elq_egid' => 'Eloqua GUID',
0. 'faaspre_elq_ecaid' => 'Eloqua Campaign ID',
0. 'faaspre_custom_vc_1' => 'Custom Text 1',
0. 'faaspre_custom_vc_2' => 'Custom Text 2',
0. 'faaspre_custom_vc_3' => 'Custom Text 3',
...
0. 'faaspre_custom_text_20' => 'Custom Textarea 20',
0. 'faaspre_date_created' => 'Date Created',
0. 'faaspre_date_modified' => 'Date Modified',
0. 'faaspre_user_created' => 'User Created',
0. 'faaspre_user_modified' => 'User Modified',


* * *
#### 2. HTML
----

##### 2.1 Form Validation 

Every form needs to have form validation. Forms are validated two ways:

0.  HTML5 Form Validation
0.  vivintFormManager.js

>  Additional validation should NOT be necessary.

> Don't use inline JavaScript to submit forms.

*Example: Bad Form*

`html
<a href="javascript:{}" class="button " onclick="document.getElementById('form38').submit();">Submit</a>
`

*Invalid Field Messages*

0.  HTML5 Validation will display messages. Search "HTML5 validation" if you don't know how to use them.
0.  vivintFormManager.js will add a class ".problem" to the invalid input.
0.  vivintFormManager.js will display an error method (this is currently NOT in use).

##### 2.2 Basic From Validation 

Refer to vivintFormManager for all validation requirements.

The following input fields are required:

0. FaasSubmission[faasub_name_full] *or first and last name*
1. FaasSubmission[faasub_name_first]
2. FaasSubmission[faasub_name_last]
3. FaasSubmission[faasub_phone]
  * Input length: 10-18 (min-max) (Both min and max are required.)
4. FaasSubmission[faasub_postal] or postal
  * Input length: 5-14 (min-max) (Both min and max are required.
5. FaasSubmission[faasub_email] or email
  * Regex is used to determine if valid address


##### 2.3 DMP

The following form is the primary form in DMP:

> v_id 97 FORM: Primary Sales

##### 2.4 HTML5 Regex 
  
> html5 Phone  RegEx = [\d|\.|\s|\-|\+|\(|\)]{10,18}

`<input type="tel" pattern="[\d|\.|\s|\-|\+|\(|\)]{10,18}"`

> html5 postal Regex = [\d|\s|\-\w]{5,14}

`<input type="text" class="fassub_postal" pattern="[\d|\s|\-\w]{5,14}"`

* * *
####  3. CSS
----

When customizing forms add the custom class name to the form tag: `<form class="custom-name">` .

###### Example

*HTML*

```html
<form action="/form/capture" method="post" class="custom-class-name">
    <input type="text" class="i_text faasub_name_first" name="FaasSubmission[faasub_name_first]" placeholder="First Name" data-pp-field="pp_fname" title="First Name" required="">
    ... 
    <input type="submit" class="i_submit" name="Submit" value="Request Quote" data-eventcategory="form" data-eventaction="click" data-eventlabel="form-submit">
    <input type="hidden" class="faasub_send_to_sfdc" name="FaasSubmission[faasub_send_to_sfdc]" value="1">
 </form>
```

*CSS*

```html
form.custom-class-name {
	...
}
.custom-class-name input[type="text"] {
	...
}
.custom-class-name input[type="submit"]{
	...
}
```

Various CSS classes used in forms (mainly older forms using subtle_forms.js):

- subtle_form_result -> Used in the main div wrapper
- subtle_form_message -> Used for all form messages
- subtle_form -> Used with the <form> tag
- i_text -> Used with the text/tel/email input fields
- faasub_name_first
- faasub_name_last
- faasub_phone
- faasub_postal
- faasub_email ->
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

###### vivintFormManager.js

a refactored version of subtle_forms.js, is used to validate and control all form submission.  *vivintFormManager.js* is used to pre-populate fields, run validation, show error messages and submit the form. It uses the same regexs as the HTML5 patterns. *vivintFormManager.js* is used on the 2014 pages. Older pages use the *subtle_forms.js* for validation.

###### campaigns.js

defines dataLayer global variable. Defines global default cookies, sets domain codes all items used for campaign tracking.

* * *
####  4. Analytics
----

*Forms*

1. SaleForce - Main system used to store & work with leads & customers.
2. Eloqua - Used for nurturing and remarketing ("Faas" prefix is used for Eloqua)

*Page*

1. Google Analytics - 
2. Site Catalyst - 
3. Optimizely - Used for test data and conversion rates
4. Test & Target - 

