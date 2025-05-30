# Block Patterns and Templates in JCORE®

## Why Block Patterns?

They let you easily create a complex layout of blocks in a matter of seconds and save it like a template. You can then
use these patterns anywhere on the website to recreate repeating sections with minimal effort.

## Creating a Block Pattern

Block patterns are created using the plugin Pattern Manager which is included in new JCORE® projects by default. It adds
a Pattern menu item in the backend where you can create new patterns in Gutenberg. It lets you choose the name and
category of the pattern you are creating.

When saved the pattern can be found in the `patterns` folder in the root of the enabled theme. It uses the builtin
functionality of WordPress to save and load block patterns from that folder.

WordPress [documentation](https://developer.wordpress.org/themes/advanced-topics/block-patterns/#using-the-patterns-directory-to-register-patterns)
for this can be found here.

An example of the header comment that is generated when using the plugin. Notice the automatically added `jcore` to the
Slug. It automatically adds the loaded text domain.

```
/**
 * Title: Blog Test
 * Slug: jcore/blog-test
 * Description: 
 * Categories: hero
 * Keywords: 
 * Viewport Width: 1280
 * Block Types: 
 * Post Types: post
 * Inserter: true
 */
```

## Using default block templates for new posts

Creating a block template is useful if a post type should always have a certain look. eg. products in a WooCommerce
store. Block templates can be easily created by using a block pattern like in the example below. This code would
automatically add the `jcore/blog-test` block pattern when creating a new post.

```
<?php
function register_blog_template() {
    $post_type_object = get_post_type_object( 'post' );
    $post_type_object->template = array(
        array( 'jcore/blog-test' ),
    );
}
add_action( 'init', 'jcore_child\register_blog_template' );
```

WordPress [documentation](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-templates/)
about block templates.