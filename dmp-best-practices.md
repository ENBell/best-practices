DMP Best Practices
==================

###  Philosophy
  The style guide is designed to help you & your team make better, consitent, long-term coding decisions. Better coding means code is easier to navigate, easier to learn, easier to refactor and easier to control as it grows in thousands and thousands of lines of code and increases in complexity.

#### Two major principles of good code:
#####  Discoverable
  Being able to quickly and easily determine where code is being used on a page (& vice versa) and what the code is doing is Good Coding.

#####  Modular
  Being able to change code in one place and not have it break other code is Good Coding. Being able to reuse code without having to pull in complex depencencies is Good Coding.

* * *
html Rules  
--------------------

####  1. Use a dmp view ID on all views. ??Can we automate this??

*Bad Practice*
```html
	<div id="featured" class="homepage-wrapper">...</div>
```

*Good Practice*
```html
	<div dmp_id="467" id="featured" class="homepage-wrapper">...</div>
```

> Industry standard

#### 2. Opening tags and closing tags should always be in the same file/view/

*Bad Practice*
```html
	{{view id=embed v_id=123}
	</div>
	}
```

*Good Practice*
```html
	<div dmp_id="467" id="featured" class="homepage-wrapper">...</div>
```

#### 2. Always include file name in comments when embedding a view.

*Bad Practice*
```html
	{{view id=embed v_id=123}}
```

*Good Practice*
```html
	<!-- HP:Home -->
	{{view id=embed v_id=123}}
```

#### 3.  