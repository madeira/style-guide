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

##Examples

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
