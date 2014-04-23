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

####  1. Use camelCase for variables.

*Bad Practice*
```javascript
	var random_variable,
		random_Variable_Two;
```

*Good Practice*
```javascript
	var randomVariable,
		randomVariable2;
```

> Industry standard

#### 2. All boolean variables should start with 'is'

*Bad Practice*
```javascript
	var valid = true;
```

*Good Practice*
```javascript
	var isValid = true;
```


 #### 3. Place constants or time variables (animation durations, etc.) at the top of the file.

*Good Practice*
```javascript
	var isValid = true;
```

#### 4. Never have more than one global variable.

#### 5. Use white-space and line breaks as follows:

*Bad Practice*
```javascript
	for(var i=0,j=arr.length;i<j;i++){
		// Do something.
	}
	for(var i=0,j=arr.length;i<j;i++)
	{
		// Do something
	}
```

*Good Practice*
```javascript
	for (var i = 0, j = arr.length; i < j; i++) {
		// Do something.
	}
```

6. Strive to create generalized functions that take parameters and return values. 
