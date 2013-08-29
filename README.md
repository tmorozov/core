core
====

Scalable JS architecture
[![Build Status](https://api.travis-ci.org/tmorozov/core.png)](https://travis-ci.org/tmorozov/core)

Inspired by 
* [presentation](http://www.slideshare.net/nzakas/scalable-javascript-application-architecture)
* [marionettejs](http://marionettejs.com/)

To summarize it:

1. Base library - normalizes interaction with browsers
2. Core - provides sandbox for modules, manages start/stop process of modules
3. Sandbox provides Pub-Sub mechanism, normalized interface to common stuff (AJAX, DOM manipulation, etc.)
4. Modules are responsible for displaying information on part of screen. Modules know nothing about application and other modules.
5. Communication is done on Pub-Sub basis

I loosened some rules - no need to completely normalize interaction with base library, as it's not changed n future as a fact.
I used #extend from [underscorejs](http://underscorejs.org/).
Syntax for application/modules looks like in [marionettejs](http://marionettejs.com/), but I've introduced sandbox(extendable).
No external dependancies as for now. Could be used with different Base libraries.

Include order of files
----------------------

1. include 3 party libs
2. include core.js
3. include sandbox extensions (if any)
4. include app definition
5. include modules (as modules depend on sundbox & application)

```html
<script src="/javascripts/3_party_lib.js"></script>
<script src="/javascripts/core.js"></script>
<script src="/javascripts/sandbox_extension.js"></script>
<script src="/javascripts/app.js"></script>
<script src="/javascripts/modules/contacts/main.js"></script>
<script src="/javascripts/modules/details/main.js"></script>
<script src="/javascripts/modules/menu/main.js"></script>
<script src="/javascripts/modules/toolbar/main.js"></script>
```

If module consists of many files, you should manage order by hand. For example if view depends on collection,
collection depends on model, you could include them as here
```html
<script src="/javascripts/modules/contacts/model.js"></script>
<script src="/javascripts/modules/contacts/collection.js"></script>
<script src="/javascripts/modules/contacts/view.js"></script>
<script src="/javascripts/modules/contacts/main.js"></script>
```

Example with DHTMLX as base library. [core + DHTMLX](https://github.com/tmorozov/dhtmlx-node)

TODO
----
* implement module#stop
* implement sub-modules
* improve test coverage
* code examples in readme
