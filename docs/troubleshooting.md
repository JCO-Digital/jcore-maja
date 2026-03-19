# Troubleshooting

## Fixing \_load_textdomain_just_in_time

This section will tell you how to fix the textdomain load error. This is not a critical one to fix, but it's always good to get it done, and you will get rid of the error messages.

```
Notice
: Function _load_textdomain_just_in_time was called
incorrectly
. Translation loading for the
jcore
domain was triggered too early. This is usually an indicator for some code in the plugin or theme running too early. Translations should be loaded at the
init
action or later.
```

### Root of the problem

The main cause of the problem is that the text_domain is loaded too early. In the case of JCORE this is usually because some of the classes and functions are called directly from the functions.php file, and not through a hook.

### JCORE 3

Since JCORE Ilme is copied to a project at the project start, it's unfortunately not possible to fix it once in one place, but it needs to be fixed in each project. Luckily this is not very hard to do.

#### Gintonic

This branch uses Timber to render the page, and has more of the old customizer settings left, hence a bit more to fix.

##### includes/init.php

Move the `Settings::init();` call into the `after_setup_theme` hook, and change the priority to `0`.

```php
add_action(
	'after_setup_theme',
	function () {
		load_jcore_textdomain();
		Settings::init();
	},
	0
);
```

##### includes/modules.php

Wrap the `load_modules()` call in a `after_setup_theme` hook.

```php
add_action(
	'after_setup_theme',
	function () use ( $modules ) {
		load_modules( $modules );
	}
);
```

##### includes/customizer.php

Here all the functions in the file into a `after_setup_theme` action, and give is a priority of 30.
