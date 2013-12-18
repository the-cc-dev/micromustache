#MicroMustache

A stripped down version of the {{mustache}} template engine with JavaScript.
It covers the most important use case for Mustache: replacing variables with their names.
MicroMustache doesn't support partials, array and nested objects.
It is about 40% faster than Mustache.js and less 93% smaller!

* Tiny (less than 0.5KB)
* Super-Quick (just one function call over the native browser layer) run the comparison live: http://jsperf.com/micromustache-vs-mustache
* Super efficient (no extra variable created, tested for memory leaks)
* Familiar to Mustache users (uses the same {{}} convention as well as the render() function)
* No dependency (No need for JQuery, Underscore, Mustache, etc)
* Cross-browser compatible
* Full test coverage with Qunit

#Consistency

For maximum consistency, MicroMustache is extensively tested against [Mustache.js] (https://github.com/janl/mustache.js).
So this can be used as a drop-in replacement for the full blown heavy Mustache or Handlebars for that matter.

#Why?

I love Mustache but sometimes it's too big for the task in hand.
Sometimes all I need is a small, simple, quick and robust text replacement.

#Why not?

MicroMustache is a super quick and super small Mustache implementation.
To achieve this speed and size, some of Mustache's features are eliminated:

* No iteration over array elements. {{#arrName}} doesn't work
* No access to object properties. {{objName.propertyName}} doesn't work
* No partials. {{>partialName}} doesn't work
* HTML sanetization (you can sanetize it externally if you want). {{{propertyName}}} doesn't work.
* Inverted selection
* Set delimiters (you can edit and modify the source code to change it though)
* Currently variable names can only be alphanumeric (a-z, A-Z, 0-9), no $ or _ or other unicode characters

The algorithm is optimized for quick execution and if your data is anything more complicated than a flat
dictionary you can use any other alternatives including Mustache.js itself.

#FAQ

## What's different from Mustache?

* only alphanumeric characters are allowed in a variable's name (dollar sign or underline is not allowed)
* variable names can begin with numbers (but the corresponding key needs to be the string equivalent of that number)

## What features are present?

The following features however are present (and shared with Mustache):

* Marking variables with {{}}
* Replacing string values
* Replacing numerical values
* Replacing boolean values
* Replacing function values. The function will be called with the name of the key as its only parameter
* The render() function
* The compile() function (though they don't improve speed, but they make the repetitive code cleaner to read)
* Comments (technically anything that is not an alphanumeric variable name will be ignored)

## Why variable names cannot include $ and _ just like Javascript?

For having a faster execution, we only use the \w regular expression.
Besides every character in the code counts, so a shorter regular expression means a smaller file.

#Examples

For more examples see the MicroMustache-test.js inside the test directory above.

#Upcomming features

* Plugins to change the {{}} to another markup of your choice
* Plugin for supporting array traversal
* Plugin for supporting nested objects