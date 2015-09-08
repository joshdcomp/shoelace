Shoelace
========
This is my take on creating an OOCSS SASS framework with an emphasis on mitigating overhead for managing things like media queries, z-indices, colors, dimensions, and adding new UI components. There are some nascent opinions in the code/architecure, described below.

Files are split into `core`, `legacy`, `lib`, and `vend` directories.

- **Core** is for utility functions, general config variables, mixins, and helper classes
- **Legacy** is where all your old crusty styles live as you migrate from your old framework
- **Lib** is meant to be home for all of the actual working styles, each object (UI element) gets its own dir with a config file (to create a translation layer between global framework and semantic object-specific variable names) global stylesheet and a file for each media query (tools like Yeoman solve the problem of generating all these files)
- **Vend** any third party mixins, styles, tools, etc. Everything here should be left as-is to keep make for easy updates

##Opinions
There are several patterns/opinions I'm playing with in this framework:

###Index pattern
The framework pulls files in by having discrete indeces at each level, so `importer` only pulls in the index for `lib/index`, `lib/index` only pulls in `[ui-element]/index`, and `[ui-element]/index` pulls in the working styles and config file.

###Configuration maps
The working styles don't have many static values declared in-line.  Rather they're defined in a `config` file for each module, and as most of these values change between breakpoints, the values are stored in a map rather than static variable. This has two benefits: 1) values are easily referenced within the module (it's recommended that you avoid referencing variables across modules) 2) it's very easy to see the values for every breakpoint in one location. 

##Tidbits
- The `.gitignore` in this repo is meant to be used in concert with the global `.gitignore` for OSX suggested  [here]( https://github.com/github/gitignore/tree/master/Global)
- Markup is from HTML5 boilerplate
