# "Cuba's New Wave" Development Style Guide

## Notes for Devs
* If you don't understand something in the documentation, ask Lindsay. Don't worry too much at first about making style errors for the more complex things, we will go through and check your code frequently and help you adhere to style rules.

## Site-Specific Styles

* During development, every page will have its own CSS file, with the same name as the page template. (``inner.ejs`` matches ``inner.css``).

## Best Practices for HTML/CSS

* Element IDs and class names should always be lowercase-with-dashes. No ``camelCase``!
* Write valid semantic markup. That means a top hierarchy header is always wrapped in ``<h1>``, a paragraph is always wrapped in ``<p>``, etc.
* For our interactives: put all of the script tags right before ``</body>``, so as to not block rendering of the page.
* DO NOT USE !important.
* Avoid inline styles and style tags.
* All media queries go at the bottom of the stylesheet.
* Your custom stylesheet goes below all CSS frameworks/outside styles.
* Always be consistent with your units. Use ems for fonts and px for margin/padding. 100vw is an acceptable dimension for an image if you're trying to make it full screen width.
* Every image needs an ``alt`` tag for accessibility. We will discuss how that is templated later.

## Best Practices for Javascript

### General

* Use 4-spaces for indentation.
* Javascript variables names should always be ``camelCase`` (never ``snake_case``).
* Constant variables and configuration parameters should be in ``TITLECASE_WITH_UNDERSCORES``.
* Named functions should be declared like this ``var functionName = function() {}``.
* Event handlers should be named `on` + the name of the event generator + the event name, for example `onDocumentLoad`, `onWindowResize` and `onGoButtonClick`.
* All global variables should be defined at the top of the file.
* All variables should be constrained to the current scope with ``var``.
* Declare one variable on one line.
* End all statements with a semicolon.
* Use spaces or line breaks after opening and before closing braces and brackets in array and object definitions, i.e. ``{ foo: [ 1, 2, 3 ] }`` not ``{foo:[1,2,3]}``.
* Do not use spaces after opening or before closing parentheses, i.e. ``if (foo === true) {`` and not ``if ( foo === true ) {``. 
* Put `else` statements on the same line as the `if` block's closing `}`.
* When accessing properties of a data structure (such as one retrieved using ``getJSON``) prefer bracket syntax (``data['property']``) to attribute syntax (``data.property``).
* Very frequent property references (e.g. those inside loops) should be cached, i.e. ``var array_length = array.length;``.
* Use ``===`` rather than ``==``. ([Why?](http://www.impressivewebs.com/why-use-triple-equals-javascipt/))
* **Use single-quotes for strings.**

### Libraries

For consistency, prefer the following libraries to others that perform the same tasks:

* [jQuery](http://jquery.com/) for DOM manipulation

### jQuery-specific

* jQuery references that are used more than once should be cached. Prefix these references with ``$``, i.e. ``var $electris = $('#electris');``.
* Whenever possible constrain jQuery DOM lookups within the scope of a cached element. For example, ``$electris.find('.candidate')`` is preferable to ``$('.candidate')``.
* Always use [on](http://api.jquery.com/on/), never [bind](http://api.jquery.com/bind/), [delegate](http://api.jquery.com/delegate/) or [live](http://api.jquery.com/live/). ``on`` should also be preferred to "verb events", such as [click](http://api.jquery.com/click/).
* When an event needs to occur for elements which may not yet exist, use `on` in delegated/bubble mode, rather than binding and unbinding events as elements are created and destroyed. For example: `$wrapper.on('click', '.item', onItemClick)`.
* When using `on` for delegated/bubbled events, always use the *nearest* container div. Do not use `$body` to capture events from anywhere as this degrades performance.

## Sources
This style guide is adapted from the [NPR Apps Best Practices Style Guide](https://github.com/nprapps/bestpractices/blob/master/javascript.md) and [taitems' Front End Web Dev Guidelines](http://taitems.github.io/Front-End-Development-Guidelines/).

