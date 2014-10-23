#Coding style

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

###List @extend(s) First

    .weather {
      @extends %module;
      ...
    }

###List "Regular" Styles Next

    .weather {
      @extends %module;
      background: LightCyan;
      ..
    }

###List @include(s) Next

    .weather {
      @extends %module;
      background: LightCyan;
      @include transition(all 0.3s ease-out);
      ...
    }

This visually separates the @extends and @includes as well as groups the @includes for easier reading. You might also want to make the call on separating user-authored @includes and vendor-provided @includes.

###Nested Selectors Last

    .weather {
      @extends %module;
      background: LightCyan;
      @include transition(all 0.3s ease);

      > h3 {
        border-bottom: 1px solid white;
        @include transform(rotate(90deg));
      }
    }

###Maximum Nesting: Three Levels Deep

    .weather {
      .cities {
        li {
          // no more!
        }
      }
    }

###List Vendor/Global Dependancies First, Then Author Dependancies, Then Patterns, Then Parts

So the "table of contents" things comes together like:

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

###Break Into As Many Small Files As Makes Sense

There is no penalty to splitting into many small files. Do it as much as feels good to the project. I know I find it easier to jump to small specific files and navigate through them than fewer/larger ones.

    ...

    @import "global/header/header/";
    @import "global/header/logo/";
    @import "global/header/dropdowns/";
    @import "global/header/nav/";
    @import "global/header/really-specific-thingy/";

###Variablize All Common Numbers, and Numbers with Meaning

If you find yourself using a number other than 0 or 100% over and over, it likely deserves a variable. Since it likely has meaning and controls consistency, being able to tweak it enmasse may be useful.

If a number clearly has strong meaning, that's a use case for variablizing as well.

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
