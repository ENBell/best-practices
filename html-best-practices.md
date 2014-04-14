HTML Best Practices
==================

###  Philosophy
  The style guide is designed to help you & your team make better, consitent, long-term coding decisions. Better coding means code is easier to navigate, easier to learn, easier to refactor and easier to control as it grows in thousands and thousands of lines of code and increases in complexity.

#### Two major principles of good code:
#####  Discoverable
  Being able to quickly and easily determine where code is being used on a page (& vice versa) and what the code is doing is Good Coding.

#####  Modular
  Being able to change code in one place and not have it break other code is Good Coding. Being able to reuse code without having to pull in complex depencencies is Good Coding.

* * *
HTML Rules
--------------------

####  1. Don't write inline styles, unless your coding for email.

*Bad Practice*
```html
<div style="font-family:normal 16px/26px Arial,adelle-sans,sans-serif; font-size: 14px; color: black; ">Heading Text</div>

```

*Good Practice*
```html
<div class=".s3-text">Heading Text</div>
.s3-text {
	font-family:normal 16px/26px Arial,adelle-sans,sans-serif;
	font-size: 14px; 
	color: black; 
}
```

> IDs are for JavaScript :)

> Unique class names are good Practice
