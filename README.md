Triple Pattern Fragments Client
===============================

A JavaScript client to a [Triple Pattern Fragments][] server.


The client is written in such a way that it can be used in the browser or using
[Node][] without modification. It features a [fluent interface][] and uses
caching to eliminate redundant calls to the server.


[fluent interface]: https://en.wikipedia.org/wiki/Fluent_interface
[Node]: https://nodejs.org
[Triple Pattern Fragments]: http://linkeddatafragments.org/


Quickstart
----------

Download `src/tpf.js` and include it in your HTML:

    <script href="tpf.js"></script>
    <script>
        const rdfs = "http://www.w3.org/2000/01/rdf-schema#"

        const endpoint = "http://openvivo.org/tpf/core"
        const client = new tpf.Client(endpoint)

        client
            .Entity("http://openvivo.org/a/orcid0000-0002-1304-8447")
            .Link(rdfs, "label")
            .Single(function (label) { console.log(label) })
    </script>



Development
-----------

We are using GitHub for issue tracking and collaborative development.

Explore the ideas under [`examples/`](examples/).

If you don't already have a code editor, we recommend [Visual Studio Code][].
We use [JSDoc][] for documenting the code, which allows for nice features that
aid in development such as autocompletion.

[JSDoc]: https://jsdoc.app/
[Visual Studio Code]: https://code.visualstudio.com/


Testing
-------

Testing requires [NodeJS](https://nodejs.org) and the
[MochaJS](https://mochajs.org/) testing framework.

On the command line, run the following commands:

    $ npm install
    $ npm test

Note: while the code under `src/` needs to support older browsers, the code
under `tests/` has no such requirement. So, feel free to use all the arrow
functions and object destructuring that newer versions of JavaScript have.


Conventions
-----------

JavaScript is a multi-paradigm language. As a result, there are many different
idioms, patterns, and styles. In an effort to ease development and provide
consistency, here are the conventions used.

 * Related code should be grouped and separated into their own `.js` file,
   called **modules**.
 * Modules must have the following parts:
   * `"use strict"` declaration;
   * NodeJS-compatible imports section;
   * namespace declaration (where the functions and objects are defined);
   * NodeJS-compatible exports section;
 * Exported (public) names should begin with a capital letter.
 * Unexported (private) names should not be capitalized.

As for formatting, use Visual Studio Code's builtin formatter. Also,

 * No semi-colons.
 * Use double-quotes `"` for strings, not single `'`'.
   * Exception: the string contains a `"` or is a single character.
