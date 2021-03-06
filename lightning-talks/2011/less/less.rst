LESS
===================================

Julia Elman

December 08, 2011

----

Overview
-----------------------------------

----

Overview
-----------------------------------

* What is LESS?

----


Overview
-----------------------------------

* What is LESS?
* Why would I want to use it?

----

Overview
-----------------------------------

* What is LESS?
* Why would I want to use it?
* Tools that make your life easier

----


What is LESS?
-----------------------------------

----

What is LESS?
-----------------------------------

A dynamic stylesheet language that uses CSS syntax to create variables, mixins, operations and functions for your stylesheets.

----


What the heck does that mean?
-----------------------------------

.. image:: scratching-head.jpg

----


Variables
-----------------------------------

----

Variables
-----------------------------------

Variables allow you to specify widely used values in a single place, and then re-use them throughout the style sheet, making global changes as easy as changing one line of code.

----

Variables example
-----------------------------------

LESS Syntax

 @blue: #0066CC;
 
 section { background-color: @blue; }

 a { color: @blue; }

CSS Output

 section { background-color: #0066CC; }

 a { color: #0066CC; }

----

Mixins
-----------------------------------

----

Mixins
-----------------------------------

Mixins allow you to embed all the properties of a class into another class by simply including the class name as one of its properties.

----

Mixins example
-----------------------------------

LESS Syntax::

 | .box-shadow(@shadow:8px 5px 5px #ccc) {
 | -webkit-box-shadow: @shadow;
 | -moz-box-shadow: @shadow;
 | box-shadow: @shadow; }

 section { .box-shadow; }

 section.place { .box-shadow(10px 5px 5px #ddd); }

CSS Output::

 | section { 
 |  -webkit-box-shadow: 8px 5px 5px #ccc;
 |  -moz-box-shadow: 8px 5px 5px #ccc;
 |  box-shadow: 8px 5px 5px #ccc; 
 | }

 | section.place { 
 | -webkit-box-shadow: 10px 5px 5px #ddd;
 | -moz-box-shadow: 10px 5px 5px #ddd;
 | box-shadow: 10px 5px 5px #ddd; }

----

Nested Rules
-----------------------------------

----

Nested Rules
-----------------------------------

Rather than constructing long selector names to specify inheritance, in Less you can simply nest selectors inside other selectors. This makes inheritance clear and style sheets shorter.

----

Nested example
------------------------------

LESS syntax::

 header {
    h1 {
        | font-size: 26px;
        | font-weight: bold; }
        | p { font-size: 12px;
        | a { text-decoration: none;
        | &:hover { border-width: 1px } 
    | } } 
    | }

CSS Output::

 header h1 {
    | font-size: 26px;
    | font-weight: bold; }

 | header p { font-size: 12px; }
 | header p a { text-decoration: none; }
 | header p a:hover { border-width: 1px; }

----

Operations
-----------------------------------

----

Operations
-----------------------------------
Are some elements in your style sheet proportional to other elements? Operations let you add, subtract, divide and multiply property values and colors, giving you the power to create complex relationships between properties. 

----

Operations example
-----------------------------------

LESS Syntax::

 | @the-border: 1px;
 | @base-color: #111;
 | @dark-red: #CD0000;
 | @yellow: #FFFF00;

 section.operations {
   | color: @base-color * 3;
   | border-left: @the-border;
   | border-right: @the-border * 2;
   | border-color: @dark-red;
   | background-color: @yellow; }

CSS Output::

 section.operations {
    | color: #333333;
    | border-left: 1px;
    | border-right: 2px;
    | border-color: #cd0000;
    | background-color: #ffff00; }

----

Why would I want to use it?
----------------------------------

----

Why would I want to use it?
----------------------------------

* Create "less" lines of code you have to write

----

Why would I want to use it?
----------------------------------

* Create "less" lines of code you have to write
* Passing off code to others is easier

----

Why would I want to use it?
----------------------------------

* Create "less" lines of code you have to write
* Passing off code to others is easier
* More readable

----

No more matrix-like stylesheets!
----------------------------------

.. image:: matrix.jpg
    :width: 100%

----

Client side usage
----------------------------------

Place your less file and the less.js file in your head::

 | <link rel="stylesheet/less" type="text/css" href="styles.less">
 | <script src="less.js" type="text/javascript"></script>

----

Server side usage - Django
----------------------------------

Install node.js and npm (http://npmjs.org/)

Install the command-line less compiler::

 npm install --global less

Add lessc to COMPASS_PRECOMPILERS in your settings file::

 COMPRESS_PRECOMPILERS = (
  ('text/less', 'lessc {infile} {outfile}'),
 )

Example of usage in template::

 {% load compress %}

 {% compress css %}
 <link type="text/less" rel="stylesheet" href="/static/css/styles.less" charset="utf-8">
 {% endcompress %}

 // Which would be rendered into something like so:

 <link rel="stylesheet" href="/static/CACHE/css/8ccf8d877f18.css" type="text/css" charset="utf-8">

----


Or make your life even easier...
----------------------------------

* LESS.app http://incident57.com/less/ (OSX only)
* Simpless http://wearekiss.com/simpless (OSX, Windows and Linux!)

----

References
----------------------------------

* http://lesscss.org

* http://django_compressor.readthedocs.org/en/latest/settings/#compress-precompilers

* http://stackoverflow.com/questions/6928914/django-mac-osx-how-to-use-less-css

