Shoelace
========
My take on OOCSS, emphasis on mitigating overhead for managing things like media queries, z-indices, colors, dimensions, and adding new UI components.

Files are split into `core`, `legacy`, `lib`, and `vend` directories.

- **Core** is for utility functions, general config variables, mixins, and helper classes
- **Legacy** is where all your old crusty styles live as you migrate from your old framework
- **Lib** is meant to be home for all of the actual working styles, each object (UI element) gets its own dir with a config file (to create a translation layer between global framework and semantic object-specific variable names) global stylesheet and a file for each media query (tools like Yeoman solve the problem of generating all these files)
- **Vend** any third party mixins, styles, tools, etc. Everything here should be left as-is to keep make for easy updates

The framework pulls files in by having discrete indeces at each level, so `importer` only pulls in the index for `lib/index`, `lib/index` only pulls in `[ui-element]/index`, and `[ui-element]/index` pulls in the working styles and config file.

##Tidbits
- The `.gitignore` in this repo is meant to be used in concert with the global `.gitignore` for OSX suggested  [here]( https://github.com/github/gitignore/tree/master/Global)
- Markup is from HTML5 boilerplate
