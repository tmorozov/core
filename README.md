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

Example with DHTMLX as base library. [core + DHTMLX](https://github.com/tmorozov/dhtmlx-node)

TODO
----
* implement module#stop
* implement sub-modules
* improve test coverage
