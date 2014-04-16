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

####  1. Don't use inline styles, unless your coding for email.

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

#### 2. Avoid unecessary nesting of single div tags.

*Bad Practice*
```html
<div class="main-wrapper">
	<div class="content">
		<div class="main-content">
			<div class="marketing-box">
				<div class="left-side">...</div>
				<div class="right-side">...</div>
			</div>
		</div>
	</div>
</div>

```

*Good Practice*
```html
<div class="main-wrapper">
	<div class="marketing-box">
		<div class="left-side">...</div>
		<div class="right-side">...</div>
	</div>
</div>
```

*Better Practice*
```html
<div class="main-wrapper marketing-box">
	<div class="left-side">...</div>
	<div class="right-side">...</div>
</div>
```

#### 2. Avoid more than 3 class names. Create unique class.

*Bad Practice*
```html
<div class="main-box left marketing-style short-from-style">
</div>

```

*Good Practice*
```html
<div class="marketing-form-2">
</div>
```

#### 3. Don't write text in all caps.

*Bad Practice*
```html
<h1>START SAVING TODAY!</h1>
```

*Good Practice*
```html
<h1>Start Saving Today!</h1>
```

#### 4. Don't use tables for page layout. Unless working with emails.

#### 5. When commenting closing div's include the id or name.

*Bad Practice*
```html
	<div id="master-wrapper">
	...
	</div> <!-- /master-wrapper -->
	<div class="content">
	...
	</div> <!-- /content -->
```

*Good Practice*
```html
	<div id="master-wrapper">
	...
	</div> <!-- /#master-wrapper -->
	<div class="content">
	...
	</div> <!-- /.content -->
```

