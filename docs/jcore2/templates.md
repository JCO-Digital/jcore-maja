# Twig Templates
The jcore twig templates are located in the 'views' folder in both jcore2 and the project child theme. Templates in the child theme override the templates of the same name in the jcore2 theme.

## Header & Footer
We now use the WordPress standard of calling `get_header();` and `get_footer();` in the PHP templates and not in the twig files. Example from `singular.php`
```
get_header();
Timber::render( $templates, $context );
get_footer();
``` 

## The _base Templates
Some templates have a version ending in _base. This is so that the child theme template can do a partial override. The _base templates are paired with an extending template of the same name without the _base part that should be empty. In some cases where there are many similar versions, more than one template can extend the _base template.

The _base templates should almost never be overridden in the child theme. They don't really serve any purpose on the final level of inheritance. If you need to rewrite the entire template, just rewrite the template without the _base name, and leave out the extends part.

## Template Folders
The templates are organized into a folder structure to make them easier to find. Generally the root folder contains full templates, and the sub-folders contains partial templates.

### Root views Folder
Contains full templates that are called directly by Timber, and defines the entire page. There are two notable exceptions to the full page rule, the header.twig and footer.twig templates are used by the get_header() and get_footer() functions to preserve maximum compatibility with plugins.

* 404.twig - The standard page not found template.
* archive.twig - WP archive template.
* archive-dynamic.twig - Custom jcore archive loader template for a JS based archive written with Vue.js.
* author.twig - WP Author page.
* footer.twig - Template used by standard WP footer.php. This one is just a stub, and probably shouldn't be modified.
* header.twig - Template used by standard WP header.php. This should probably not be modified. You can add things to the head by adding "partials/head_custom.twig".
* layout.twig - This is the base template for the page layout. Most other templates in the root folder extend this one.
* page.twig - Template for WP page. Defaults to standard layout with page title removed.
* password-protected.twig - Template for WP password-protected pages when asking for password.
* posts.twig - Template for WP posts page. Extends archive.twig by default.
* search.twig - Template for WP search page.
* single.twig - Template for WP post single page.
* single-bbpress.twig - ????
* single-ld.twig - Template for LearnDash singles.
* single-tribe.twig - ????
* template-vue.twig - Page template that loads a Vue.js app.

### Blocks Folder
Contains the templates for custom Gutenberg blocks.

### Images Folder
Contains images (inline SVG) or image related templates.

* footer-brand.twig - Logo displayed in footer.
* image.twig - Template for displaying Timber images.
* navbar-brand.twig - Logo displayed in navbar.

### Navigation Folder
Contains all templates related to navigational menus. These are all partials, but encompass everything from the entire menu, to single items.

* desktop.twig - The desktop menu.
* item.twig - A generic partial for menu items. Recursively calls itself for submenus.
* mobile.twig - The mobile menu.
* scroll-to-top.twig - Scroll to top button.
* topbar.twig - Top menu that defaults to secondary menu.

### Partials Folder
Contains partial templates that don't fit specifically into any of the other folders.

* footer.twig - This is the visible page footer.
* footer-form.twig - Questioning if this should be there.
* footer-social.twig - This seems to be only used in a custom block.
* google-analytics.twig - Google analytics gtag template.
* google-tag-manager.twig - Google tag manager template.
* google-tag-manager-noscript.twig - Google tag manager noscript template.
* pagination.twig - Classic pagination for archive and such.
* search.twig - Search box template.
* social-media-share.twig - Social media share links for posts.
* tease.twig - Article tease template.

### Woo Folder
Contains WooCommerce templates. This folder is a bit of an exception to the rule in the sense that the root woo folder contains full templates, and it has its own structure of sub-folders.
