# Class Autoloading

Classes under the `jcore` or `jcoreBlocks` namespaces are autoloaded when used.

They are loaded from two different places depending on their namespace.

### JCORE® namespaced classes
`jcore` namespaced classes are loaded from either the child theme folder or the JCORE™ folder:

* `<theme>/classes/class-[classname].php`
* `jcore2/classes/class-[classname].php`

### JCORE® Blocks namespaced classes.
`jcoreBlocks` namespaced classes are loaded from based on an array from the filter: `jcore_blocks_folders`.
The defaults for this filter are:

* `<theme>/blocks/`
* `jcore2/blocks/`

The class file name should be: `class-[classname].php`
