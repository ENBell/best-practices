JavaScript Best Practices
==================

###  Philosophy
  The style guide is designed to help you & your team make better, consitent, long-term coding decisions. Better coding means code is easier to navigate, easier to learn, easier to refactor and easier to control as it grows in thousands and thousands of lines of code and increases in complexity.

#### Two major principles of good code:
#####  Discoverable
  Being able to quickly and easily determine where code is being used on a page (& vice versa) and what the code is doing is Good Coding.

#####  Modular
  Being able to change code in one place and not have it break other code is Good Coding. Being able to reuse code without having to pull in complex depencencies is Good Coding.

* * *
Javascript Rules
--------------------

####  1. Use camelCase for variables. '$' for jQuery object variables

*Bad Practice*
```javascript
	var random_variable,
		random_Variable_Two;

```

*Good Practice*
```javascript
	var randomVariable,
		randomVariableTwo,
		$adView = $('div.ad-view'),
		adViewValue = $adViewWrapper.val(); // no longer a jQuery object
```

> Industry standard

#### 2. Boolean variables and functions that return boolean valuse should start with 'is'

*Bad Practice*
```javascript
	var valid = true;
```

*Good Practice*
```javascript
	var isValid = true;
```

#### 4. Write documentation at the top of all JS files.

*Include*

1. General Information about the file
2. Dependencies
3. Noteworthy items
4. Cookies

```html
/*
  Used to validate all Vivint forms. 

  See the Vivint form documentation for additional information on how Vivint forms are used.

  vivintFormManager is the namespace for all other variables and functions 
  vivintFormManager calls initialize() to start the process.

  Dependecies:
  jQuery
  jQuery.validator  -> http://jqueryvalidation.org
  jQuery.placeholder  -> https://github.com/mathiasbynens/jquery-placeholder
  jQuery.cookie  -> http://plugins.jquery.com/cookie/
  Campaigns.js -> window.dataLayer 

  Cookies:
  faaspre_id
  faas
  foid
  exid

  Last Updated: April 2014
*/
```


#### 3. Avoid writing global variables.

> If you need to write global variables document it really really well. But avoid them.

#### 6. Write functional javascript

> Functions should be specialized.

*Bad Practice*
```javascript

	// setup listeners
	...
	// Check for conditions
	...
	// More Stuff

```

*Good Practice*
```javascript
	function setupListeners () {
		// DOM manipulation
		...
	}
	function isValid () {
		// validation
		...
	}
	function moreStuff () {
		// More Stuff
		...
	}
```
