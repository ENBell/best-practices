CSS Best Practices
===========

Philosophy
----------
The style guide is designed to help you make better long term coding decisions. This guide will help you write code that can be ea

Discoverable
----------
Being able to quickly and easily determine where code is being used on a page and vicaversa is Good Coding. 

Modular
----------
Being able to change code in one place and not have it break other code is Good Coding.

Refactorable
----------


1.  Don't use #ids. Use class, tag and universal rules only.

### Bad
	#home-page-nav
	footer#home-page

### Good
	.home-page-nav
	footer:after
	[hidden="true"]

## IDs are for JavaScript
## Unique class names are good	

1.  Use '-' hyphens. Not camelCase or under_score to name classes.

### Bad
	.homePageBox
	.home_page_box

### Good
	.home-page-box

1.  Don't nest identifiers more than 3 layers deep.

### Bad
	.header .nav ul li .special-class {}

### Good 
	.header .nav .special-class

### Best
	.special-class	

1.  Nest as little as possible. Don't use nestings for location finding. Use notes for location.

### Pretty Good
	.header .nav .special-class

### Better
	.nav .special-class

### Best
	/* .header .nav */
	.special-class

1.		

1.  Don't use !important;

### !important; is used for testing and quick changes NOT production.

1. AVOID using z-index.

### Refactor and Write better HTML before thinking you need z-index

1. Only use the following z-index numbers, after you've refactored your HTML:
*	100
*	200
*	300


1. Make note of CSS dependant code (avoid it when possible.). Use inherit.

### Bad
	.parent-box {
	  width: 100px;
	}
	.parent-box .left-side {
		width: 200px;
	}
	.parent-box .right-side {

	}


### Good

1. Don't repeat code. If you refactor and check new code against previously written code before

### Bad
line 45 .great-deal-text {
			font-weight: bold;
			font-size: 1.2em;
			line-height: 1.2em;
		}

line 178 .testimonial-header-text {
			line-height: 1.2em;
			font-weight: bold;
			font-size: 1.2em;
		}
	

### Good

line 45 .large-bold-text {
			font-weight: bold;
			font-size: 1.2em;
			line-height: 1.2em;
		}
		

1. Always comment major code break sections.

/***** Header Start *****/
...
/***** Header End *****/

/***** Footer Start *****/
...
/***** Footer End *****/

1. Don't use negative margins.

### Bad 
	.menu-item h1 {
		margin-top: -5px;
		line-height: 1.3em;
	}

### Good 
	.menu-item h1 {
		margin-top: 0;
		line-height: 1em;
	}	

1. Don't put values on 0.

### Bad 
	.menu-item h1 {
		margin-top: 0px;
	}

### Good 
	.menu-item h1 {
		margin-top: 0;
	}

1. Separate your CSS files into logical, modular files.

### Good
	Separating your homepage css (home-page.css) from your global css (global.css).
	Creating a separate file for forms (forms.css).
	Modular files mean the file can work well independently. Files should have no more than one depency files (global.css).

### Bad
	Duplicating css in different files. 
	If you find repeated code in 


