CSS Best Practices
==================

###  Philosophy
  The style guide is designed to help you & your team make better, consitent, long-term coding decisions. Better coding means code is easier to navigate, easier to learn, easier to refactor and easier to control as it grows into thousands and thousands of lines of code and increases in complexity.

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

> __!important__ is used for testing and quick changes in the browser NOT production.
> Using __!important__ creates unecessary __!important__ chaines.

#### 6. AVOID using z-index.

> Refactor and write better HTML before thinking you need z-index

##### Only use the following three z-index numbers, after you have refactored your HTML:

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

#### 7. Don't repeat code.

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

#### 8. Every CSS file should have an index and section code breaks.

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

> This will help to separate files as content expands.

#### 9. Don't use negative margins to overwrite refactorable code or compensate for padding.

*Bad Practice*
```css 
	.menu-item h1 {
		margin-top: -5px;
		padding: 10px 0;
	}
```

*Good Practice*
```css 
	.menu-item h1 {
		padding: 10px 0 5px 0;
	}
```

> Negative margins may be used to position backgrounds or center absolute positioned elements, but try to avoid them.

#### 10. Don't put values on 0.

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

#### 11. Understand naming conventions & think about why you are naming a class a certain way.

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

> Classes with one attribute should be named after the attribute.
 
*Tag Names*
```css 
h1,
.h1 {
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
.holiday-form {
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

> Think about what the name implies for others reading your code.

#### 12. Separate your CSS files into logical, modular files.

*Good Practice*
> Separating your homepage css (home-page.css) from your global css (global.css).
> Creating a separate file for forms (forms.css).
> Modular files mean the file can work well independently. Files should have no more than one depency files (global.css).

*Bad Practice*
> Duplicating css in different files. 
> If you find repeated code in different files.

#### 13. Don't add arbitrary values on tags.

 *Bad Practice*
```css 
img {
	float: left;
	margin-top: 6px;
}
```

*Good Practice*
```css 
img.solar-marketing-display {
	float: left;
	margin-top: 6px;
}
```
