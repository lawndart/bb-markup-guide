HTML Style Guide
============================

*Best practices and guidelines for writing HTML with approachable formatting, syntax, and more.*

Table of Contents
-----------------

1. [General Principles](#general)
2. [Doctype](#doctype)
3. [Semantics](#semantics)
4. [General Formatting](#formatting)
    - [Spacing and Indentation](#spacing)
    - [Capitalization](#capitalization)
    - [Quotation](#quotation)
    - [Lean Markup](#lean)
5. [Layer Separation](#separation)


<a name="general">General Principles</a>
-----------

**Be consistent.** If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.

<a name="doctype">Doctype</a>
-----------
HTML5 is preferred for all HTML documents:
```HTML5
<!DOCTYPE html>
```
It’s recommended to use HTML, as text/html. Do not use XHTML. XHTML, as application/xhtml+xml, lacks both browser and infrastructure support and offers less room for optimization than HTML.

<a name="semantics">Semantics</a>
-----------
Use elements (sometimes incorrectly called “tags”) according to its purpose. This is important for accessibility, reuse, and efficiency. For example, use `<header>` for headings, `<p>`
elements for paragraphs, `<a>` elements for anchors, etc.

```HTML5
// bad
<div class="header"><h1>Primary Header</h1></div>

<strong class="primary-title">This is a title</strong>

<span onclick="goToRecommendations();">All recommendations</span>

// good
<header>
  <h1>Primary Header</h1>
</header>

<h1>This is a title</h1>

<a href="recommendations/">All recommendations</a>

```

- Use list elements `<ul>`, `<ol>`, or `<dl>`. Never use a set of `<div>` or similar elements.
- Avoid trailing slashes in self-closing elements like `<img>`, `<input>`, etc.
- Form inputs with text attached should use a `<label>` element.

<a name="formatting">General Formatting</a>
----------


### <a name="spacing">Spacing and Indentation</a>

Indentation should be **two spaces**. If using tabs in a code editor, ensure that tabs are set to two spaces. Use a new line for every block, list, or table element.  Be sure to remove trailing white spaces. Trailing white spaces are unnecessary and can complicate diffs.

```HTML5
// bad
<ul> <li>Element</li><ul>

<ul> <li> Element<li>
<li>Element 2</li>
</ul>


// good
<ul>
  <li>element</li>
  <li>element 2</li>
</ul>

```

### <a name="capitalization">Capitalization</a>

All markup should be lowercase. This applies to HTML element names, attributes, properties, and property values.

```HTML5
// bad
<A HREF="/">Home</A>

<IMG src="google.png" ALT="Google">

// good
<a href="/">Home</a>

<img src="google.png" alt="Google">

```

### <a name="quotation">Quotation</a>

Even though quotes around attributes is optional, always put quotes around attributes for readability.
- Use double quotation `("")` rather than single quotation marks `('')` around attribute values.

### <a name="lean">Lean Markup</a>

When possible, avoid superfluous parent elements when writing HTML. Deeply nested elements can create challenges with styling, behavior, debugging, and are often unnecessary.  
```HTML5
// bad
<span class="avatar">
  <img src="...">
</span>

// good
<img class="avatar" src="...">

```

<a name="separation">Layer Separation</a>
----------
Keep structure(markup),presentation(styling)and behavior(scripting) apart from one another. Documents and templates should only contain HTML, and HTML that is strictly serving structural purposes. Styling and behaviors should be contained in unique files to be referenced in the head or footer of the HTML document. Mixing structure, styling and behavior together becomes incredibly difficult to update and maintain.

Additionally, keep the document as clean as possible by linking as few stylesheets and scripts as possible from templates and documents.

```HTML5
// bad
<!DOCTYPE html>
<title>HTML sucks</title>
<link rel="stylesheet" href="base.css" media="screen">
<link rel="stylesheet" href="grid.css" media="screen">
<link rel="stylesheet" href="print.css" media="print">
<h1 style="font-size: 1em;">HTML sucks</h1>
<p>I’ve read about this on a few sites but now I’m sure:
  <u>HTML is stupid!!1</u>
<center>I can’t believe there’s no way to control the styling of
  my website without doing everything all over again!</center>

// good
<!DOCTYPE html>
<title>My first CSS-only redesign</title>
<link rel="stylesheet" href="default.css">
<h1>My first CSS-only redesign</h1>
<p>I’ve read about this on a few sites but today I’m actually doing it: separating concerns and avoiding anything in the HTML of my website that is presentational.</p>
<p>It’s awesome!</p>

```
