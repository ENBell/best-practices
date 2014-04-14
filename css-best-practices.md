CSS Best Practices
==================

###  Philosophy
  The style guide is designed to help you & your team make better, consitent, long-term coding decisions. Better coding means code is easier to navigate, easier to learn, easier to refactor and easier to control as it grows in thousands and thousands of lines of code and increases in complexity.

#### Two major principles of good code:
#####  Discoverable
  Being able to quickly and easily determine where code is being used on a page (& vice versa) and what the code is doing is Good Coding.

#####  Modular
  Being able to change code in one place and not have it break other code is Good Coding. Being able to reuse code without having to pull in complex depencencies is Good Coding.

* * *
CSS Rules
--------------------

####  1. Use class, tag and universal rules only. Don't use #ids.

*Bad Practice*
```css
#homepage-nav {}
footer#home-page {}
```

*Good Practice*
```css
.homepage-nav {}
footer:after {}
[hidden="true"] {}
```

> IDs are for JavaScript :)

> Unique class names are good Practice

####  2. Use '-' hyphens for class names. Don't use camelCase or under_score.

*Bad Practice*
```css
.homePageBox
.home_page_box
```

*Good Practice*
```css
.homepage-box
```

####  3. Don't nest identifiers more than 3 layers deep. Nest as little as possible.

*Bad Practice*
```css
.header .nav ul li .special-class {
	...
}
```

*Good Practice*
```css 
.header .nav .special-class {
	...
}
```

*Best Practice*
```css
/* Used in the .header .nav section */
.special-class {}
``` 

> Don't use nestings for location finding. Use notes for location.

####  5. Don't use !important;

*Bad*
```css
.phone-call-popup {
	color: red !important;
}
```

> __!important;__ is used for testing and quick changes in the browser NOT production.
> Using __!important;__ creates unecessary __!important;__ chaines.

#### 6. AVOID using z-index.

> Refactor and write better HTML before thinking you need z-index

#### Only use the following three z-index numbers, after you have refactored your HTML:

*Rarely Acceptable Practice*
```css
.rare-class {
  z-index: 100;
}
.rare-class {
  z-index: 200;
} 
.rare-class {
  z-index: 300;
}
```
> HTML tags that are 1) nested and 2) written later in the document will be placed on top of previous HTML tags creating a natural z-index. By writing better HTML you can avoid z-index.
> z-indexes often create a chain dependent z-indexes; when you add new elements and refactor old elements you are required to re-write previously written z-indexes. z-index: 9999 = bad code. 

#### 7. Make note of CSS dependant code (avoid it when possible.). Use inherit.

*Bad Practice*
```css
.parent-box {
  font-size: 14px;
}
.parent-box .left-side {
  font-size: inherit;
}
.parent-box .right-side {
	font-size: 16px;
}
```

*Good Practice*
```css
.parent-box {
  font-size: 14px;
}
/* .left-side font-size should always match the parent box
.parent-box .left-side {
  font-size: inherit;
}
.parent-box .right-side {
	font-size: 16px;
}
```

> Learning to use __inherit__ will help you significantly.

#### 8. Don't repeat code.

*Bad Practice*
```css
line 45>> .great-deal-text {
	font-weight: bold;
	font-size: 1.2em;
	line-height: 1.2em;
}

line 178>> .testimonial-header-text {
	line-height: 1.2em;
	font-weight: bold;
	font-size: 1.2em;
}
```

*Good Practice*
```css

line 45>> .large-bold-text {
	font-weight: bold;
	font-size: 1.2em;
	line-height: 1.2em;
}
```

> If you refactor and check new code against previously written code before you will find that often the code has already been written.

#### 9. Always comment major code break sections, be consistent & create indexes

```css
/***** Index *****
	1. Header
	2. Footer
***** Index End *****/

/***** Header Start *****/
	...
/***** Header End   *****/

/***** Footer Start *****/
	...
/***** Footer End   *****/
```

#### 10. Don't use negative margins.

*Bad Practice*
```css 
	.menu-item h1 {
	margin-top: -5px;
	line-height: 1.3em;
}
```

*Good Practice*
```css 
.menu-item h1 {
	margin-top: 0;
	line-height: 1em;
}
```

#### 11. Don't put values on 0.

*Bad Practice*
```css 
.menu-item h1 {
	margin-top: 0px;
}
```

*Good Practice*
```css 
.menu-item h1 {
	margin-top: 0;
}
```

#### 12. Understand naming conventions & use them wisely.

*Attribute Names*
```css 
.white {
	color: white;
}
.large-font {
	font-size: 
}
.left {
	float: left
}
.center {
	text-align: center;
}
```

> Attribute names are most often used for styling of text & image content. 

*Tag Names*
```css 
h1,
, .h1 {
	font-size: 1.2em;
}
input[type='submit'],
.submit {
	background-color: green;
}

```

*Page Names*
```css 
.home-page-box {
	margin-top: 5px;
	margin-bottom: 10px;
	padding: 5px 10px;
}
.contact-nav h1 {
	font-size: 1.2em;
}

```

> Don't use page specific names in places where a global name is more accurate

*Type Names*
```css
.cancel-button {
	display: inline-block;
	width: 400px;
	text-decoration: uppercase;
	font-weight: bold;
	padding: 10px 5px;
	margin: 10px 15px;
}
.confirmation-box {
	font-size: 1.2em;
	padding: 10px 15px;
	border: 1px solid lightgrey;
}


```

*Custom Names*
```css 
.holiday-form input[type='submit'] {
	background-color: #12345;
}
.scrim {
	position: absolute;
	top: 0;
	right: 0;
	bottom: 0;
	left: 0;
}
```

#### 13. Separate your CSS files into logical, modular files.

*Good Practice*
> Separating your homepage css (home-page.css) from your global css (global.css).
> Creating a separate file for forms (forms.css).
> Modular files mean the file can work well independently. Files should have no more than one depency files (global.css).

*Bad Practice*
> Duplicating css in different files. 
> If you find repeated code in different files.


