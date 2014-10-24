#Coding style scss

##Spacing

* Use soft-tabs with a two space indent. Spaces are the only way to guarantee code renders the same in any person's environment.
* Put spaces after : in property declarations.
* Put spaces before { in rule declarations.
* Put line breaks between rulesets.
* When grouping selectors, keep individual selectors to a single line.
* Place closing braces of declaration blocks on a new line.
* Each declaration should appear on its own line for more accurate error reporting.

##Formatting

* Use hex color codes #000 unless using rgba().
* Use // for comment blocks (instead of /* */).
* Avoid specifying units for zero values, e.g., margin: 0; instead of margin: 0px;.
* Strive to limit use of shorthand declarations to instances where you must explicitly set all the available values.

###Examples

```scss

  // Example of good basic formatting practices
  .styleguide-format {
    color: #000;
    background-color: rgba(0, 0, 0, .5);
    border: 1px solid #0f0;
  }

  // Example of individual selectors getting their own lines (for error reporting)
  .multiple,
  .classes,
  .get-new-lines {
    display: block;
  }

  // Avoid unnecessary shorthand declarations
  .not-so-good {
    margin: 0 0 20px;
  }

  .good {
    margin-bottom: 20px;
  }
```

###List @extend(s) First

```scss

  .weather {
    @extends %module;
    ...
  }
```

###List "Regular" Styles Next

```scss

  .weather {
    @extends %module;
    background: LightCyan;
    ..
  }
```

###List @include(s) Next

```scss

  .weather {
    @extends %module;
    background: LightCyan;
    @include transition(all 0.3s ease-out);
    ...
  }
```

This visually separates the @extends and @includes as well as groups the @includes for easier reading. You might also want to make the call on separating user-authored @includes and vendor-provided @includes.

###Nested Selectors Last

```scss

  .weather {
    @extends %module;
    background: LightCyan;
    @include transition(all 0.3s ease);

    > h3 {
      border-bottom: 1px solid white;
      @include transform(rotate(90deg));
    }
  }
```

###Maximum Nesting: Three Levels Deep

```scss

  .weather {
    .cities {
      li {
        // no more!
      }
    }
  }
```

###List Vendor/Global Dependancies First, Then Author Dependancies, Then Patterns, Then Parts

So the "table of contents" things comes together like:

```scss

  // Vendor Dependencies
  @import "compass";

  // Authored Dependencies
  @import "global/colors";
  @import "global/mixins";

  // Patterns
  @import "global/tabs";
  @import "global/modals";

  // Sections
  @import "global/header";
  @import "global/footer";
```

###Break Into As Many Small Files As Makes Sense

There is no penalty to splitting into many small files. Do it as much as feels good to the project. I know I find it easier to jump to small specific files and navigate through them than fewer/larger ones.

```scss
  ...

  @import "global/header/header/";
  @import "global/header/logo/";
  @import "global/header/dropdowns/";
  @import "global/header/nav/";
  @import "global/header/really-specific-thingy/";
```

###Variablize All Common Numbers, and Numbers with Meaning

If you find yourself using a number other than 0 or 100% over and over, it likely deserves a variable. Since it likely has meaning and controls consistency, being able to tweak it enmasse may be useful.

If a number clearly has strong meaning, that's a use case for variablizing as well.

```scss

  $zHeader: 2000;
  $zOverlay: 5000;
  $zMessage: 5050;

  .header {
    z-index: $zHeader;
  }
  .overlay {
    z-index: $zOverlay;
  }
  .message {
    z-index: $zMessage;
  }
```
###Best Practices

####z-index: stack
Good idea to have that stack, and use it

```scss

  $z-index-lvl-0: 0;
  $z-index-lvl-1: 10;
  $z-index-lvl-2: 20;
  $z-index-lvl-3: 30;
  $z-index-lvl-4: 40;
  $z-index-lvl-5: 50;
  $z-index-lvl-6: 60;
  $z-index-lvl-7: 70;
  $z-index-lvl-8: 80;
  $z-index-lvl-9: 90;
  $z-index-lvl-10: 100;
```
####Base color variable
Color of blocks set on global variable.
This practice give flexibility in global changes color and in local

```scss

  $bright-red: #b30015;
     
  $header-back-ground: $bright-red;

  header {
    background: $header-back-ground;
  }

```

##Coding style html

* **HTML5** - HTML5 and it's new elements make for the most beautiful HTML yet.
* **DOCTYPE** - HTML5 has the best DOCTYPE ever
* **Indentation** - Code is indented to show parent/child relationships and emphasize hierarchy, use soft-tabs with a two space indent..
* **Charset** - Declared as first thing in the head, before any content.
* **Title** - Title of the site is simple and clean. Purpose of page is first, a separator is used, and ends with title of the site.
* **CSS** - Only one single stylesheet is used (media types declared inside stylesheet), and only served to good browsers. IE 6 and below are served a universal stylesheet.
* **Body** - ID applied to body to allow for unique page styling without any additional markup.
* **JavaScript** - do not use external resources.
* **File Paths** - Site resources use relative file paths for efficiency. Content file paths are absolute, assuming content is syndicated.
* **Image Attributes** - Images include alternate text, mostly for visually impaired uses but also for validation. Height and width applied for rendering efficiency.
* **Main Content First** - The main content of the page comes after basic identity and navigation but before any ancillary content like sidebar material.
* **Appropriate Descriptive Block-Level Elements** - Header, Nav, Section, Article, Aside... all appropriately describe the content they contain better than the divs of old.
* **Hierarchy** - Title tags are reserved for real content, and follow a clear hierarchy.
* **Appropriate Descriptive Tags** - Lists are marked up as lists, depending on the needs of the list: unordered, ordered, and the underused definition list.
* **Common Content Included** - Things common across multiple pages are inserted via server side includes (via whatever method, language, or CMS that works for you)
* **Semantic Classes** - Beyond appropriate element names, classes and IDs are semantic: they describe without specifying. (e.g. "col" is much better than "left")
* **Classes** - Are used any time similar styling needs to be applied to multiple elements.
* **IDs** - Are used any time an element appears only once on the page and cannot be targeted reasonably any other way.
* **Dynamic Elements** - Things that need to be dynamic, are dynamic.
* **Characters Encoded** - If it's a special character, it's encoded.
* **Free From Styling** - Nothing on the page applies styling or even implies what the styling might be. Everything on the page is either a required site resource, content, or describing content.
* **Comments** - Comments are included for things that may not be immediately obvious upon reviewing the code.
* **Valid** - The code should adhere to W3C guidelines. Tags are closed, required attributes used, nothing deprecated, etc.

##Example

```html
<!DOCTYPE HTML>
<html>

<head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />

  <title>Portfolio | Chris Coyier</title>

  <!--[if !IE]><!-->
    <link rel="stylesheet" type="text/css" href="/css/main.css" />
  <!--<![endif]-->

  <!--[if gte IE 7]>
    <link rel="stylesheet" type="text/css" href="/css/main.css" media="screen, projection" />
  <![endif]-->

  <!--[if IE 6]>
    <link rel="stylesheet" type="text/css" href="http://universal-ie6-css.googlecode.com/files/ie6.0.3.css" media="screen, projection" />
  <![endif]-->
</head>

<body id="home">

  <header>
    <a id="logo" href="/">Site Title</a>
    <div id="slogan">web craftsman, blogger, author, speaker</div>

    <nav>
      <?php include("inc/main-menu.php"); ?>
    </nav>
  </header>

  <section class="container">

    <article>
      <h1>Hipsters</h1>

      <img src="http://chriscoyier.net/images/hipster.jpg" alt="Hipster and Company" height="120" width="570" />

      <p>You can&#8217;t dress up as a hipster for Halloween. Their attire is already so bizarre that there isn&#8217;t an
      exaggeration of it that looks like a costume. It would just look like you are another hipster about to read a poem about reading poems.</p>

      <h2>Secondary Title</h2>
      <p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.</p>
    </article>

    <article>
      <!-- Additional Article -->
    </article>

  </section>

  <aside>
    <h3>My Major Projects</h3>
    <dl>
      <dt><a href="http://aremysitesup.com">Are My Sites Up?</a></dt>
      <dd>Monitor your sites</dd>

      <dt><a href="http://css-tricks.com">CSS-Tricks</a></dt>
      <dd>A web design community</dd>

      <dt><a href="http://digwp.com">Digging Into WordPress</a></dt>
      <dd>Learn about WordPress</dd>
    </dl>
  </aside>

  <footer class="container">
    <h4>People I Enjoy</h4>
    <ul class="col">
      <li><a href="http://fastfoodreviewed.com">Jesse Lynch</a></li>
      <li><a href="http://jeffcampana.com">Jeff Campana</a></li>
      <li><a href="http://perishablepress.com">Jeff Starr</a></li>
    </ul>
    <ul class="col">
      <li><a href="http://davidwalsh.name">David Walsh</a></li>
      <li><a href="http://thestrategicretreat.com">Jeff Penman</a></li>
      <li><a href="http://http://shiftedfrequency.com">Richard Felix Jr.</a></li>
    </ul>

    <h4>Sandwiches</h4>
    <ul class="col container" id="sandwich-list">
      <li><a href="http://jimmyjohns.com">Jimmy Johns</a></li>
      <li><a href="http://subway.com">Subway</a></li>
      <li><a href="http://potbelly.com">Potbelly</a></li>
    </ul>

    &copy;2007-<?php echo date("Y"); ?> Chris Coyier
  </footer>

  <script type="text/javascript" src='http://ajax.googleapis.com/ajax/libs/jquery/1.3.2/jquery.min.js?ver=1.3.2'></script>
  <script type='text/javascript' src='/js/main.js'></script>

  <!-- Google Analytics Code -->
  <?php include_once("inc/analytics.php"); ?>

</body>

</html>

```
