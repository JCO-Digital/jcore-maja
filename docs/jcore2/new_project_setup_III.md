# JCORE theme base styling

An example of a base style set workflow for a JCORE base project.

A more elaborate detailed list of tasks can be found in Google Docs: https://docs.google.com/document/d/1jPw7kSgcva80eQd3EZF-G2tEF2dhRTpEEbCJ5Djn6ac/edit?usp=sharing

## Mockup and stylesheet

Ask for a mockup and stylesheet in dev mode and check if the mockup has grid mode too.

If no stylesheet is available, do not start working on styles. Look through the whole mockup and stylesheet. Look for the most common colors, styles, theme, and rounded corners, and let the most common style be the primary/default/main style.
Check that colors are sufficient, as added in the previous step. If not, more colors can be added in `functions.php` via the `jcore_customizer_colors` filter.

## Colors

Theme colors are defined in the WordPress Customizer (backend). You can reference colors in SCSS using Bootstrap variables. For example, `$primary` becomes `color: var(--bs-primary)`, and so on.

If you need to add more colors to the list, you can add new variables to the `$theme-colors` list in `_colors.scss`. These new colors must also be added to the `jcore_customizer_colors` filter in `functions.php`. Use matching variable names as in `_colors.scss`.

## Fonts

If using Google Fonts, add the sizes that are present in the stylesheet and the italic versions of these. (Most changes related to fonts can be found in the variables and typography stylesheets).

- Insert sizes in variables.scss

- Decide upon a small and large font size that corresponds to a size needed.

- Insert heading-sizes in variables.scss

- Check the responsive scaling settings if `$enable-rfs: true;` is set.

- Make an example and see how the responsive scaling affects the heading sizing. Adjust with bespoke media queries if necessary.

### Line height

Check separately for headings, as the larger the font size, the smaller the spacing needs to be for a good look. Make examples of headings that span several lines.

### Font weight

Check from the mockup and add to the typography stylesheet.

### Letter-spacing

Add letter spacing to the typography stylesheet.

### Margin bottom

Set margin-bottom for all headings and for paragraphs, as well as list and link items, in the typography stylesheet. In `single.css` there are already set margin-bottoms for headings. Unify or remove them from `single.css`. It is better if all base font styling is in the typography stylesheet.

## Check container widths

Check container widths on the mockup with the grid visible. Decide on narrow and wide container widths and adjust grid breakpoints if necessary. Set group paddings to smaller/wider, depending on the general mockup look. All of these are in variables. Set all paddings and margins with the `$spacer` unit.

## Text links and their colors/behavior.

Base styles can be found last in variables.scss . Additional styling, like hover effects etc should be added to typography.

## Buttons (\_buttons.scss) will be refactored in Grasshopper with a bespoke JCORE buttons-block.

Button styling is done both for Twig/code use in "simple" form and Gutenberg use in the "more complicated form." For easier styling, different classes can be used for styling in Gutenberg and theme code. If the same classes are used, the negated button style is needed.

Special link styles are also added as buttons, even if the look is more like a text link with an animated arrow to the right/left. All these are added to the buttons.scss.

## List styling.

Check that list base styles exist and have margins and decent spacing. If they are in the stylesheet, add bullet points as in the stylesheet. If very special lists exist, add them as blocks with ACF repeater fields. If only the bullet list is present in the stylesheet, also check that the numbered list works "in the same way," with equal inline-start-padding and equal spacing. The inline-start-style can be found in `_content.scss`.

## Quotes.

Styles from the stylesheet go into `gutenberg.scss`, as Gutenberg uses quote and pullquote. Test these in Gutenberg. Come up with your own solution for the pullquote, or blacklist pullquote in `functions.php`.

## Responsive JCORE spacers (first in `gutenberg.scss`).

Adjust these to fit your theme. They work on mobile with the value set in Gutenberg and on desktop with the media query value.

## Images.

Set border-radius, shadows, layers, and spacing in text. Set these in Gutenberg and beware that Gutenberg images come in many divs ("figure", "img", etc.). Check every image type inserted and its divs.

## Box-elements in Gutenberg

Check the mockup for boxed content in Gutenberg. Set coloring and border-radius, and add classes as needed to `_gutenberg.scss`.

## Site-spanning background/front page background.

Site-spanning background images can be added to the theme in the Customizer. For special effects or color layers, the layout Twig file might need to be copied to the child theme and modified.

## Check the WP login view

What color scheme should be used? If no mockup is available, make reasonable choices. Add to variables: `$login-bg`, `$login-form`, `$login-color`. Button styles might affect the "show password" eye, so make sure to check that it is not broken.

## Footer

Special link, list, and color styling and widget areas. Social media icons. It is polite to the person coding the footer to check how the styling in the footer differs from the general color theme, list, and link styles. Possibly make the footer exceptions already at this stage in `footer.scss` (e.g., different list/link styling/coloring). This is because everything is fresh in your mind now, and you will know what to overwrite and how to achieve the new style with the least effort.

## Assets/logo SVGs

Check that all assets and logos are available for special styling, imagery, or decorative elements.

## TEST

Test all typography on a Gutenberg basic page: Lorem ipsum, all headings, paragraphs of text, lists (ul and ol), inline links, buttons, and their spacings. Also, test the responsive behavior of all these in mobile and iPad views. Some variables might need adjusting. It is alright to ask the AD or suggest changes. Nobody's perfect!

## Document

Document in the code, WP-ohjeet, or Dev-notes the classes needed in Gutenberg/code to achieve special styling.

## Core Gutenberg Blocks

Go through which Gutenberg base blocks are actually needed in the project, and blacklist the ones that are not allowed or not used in the mockup in `functions.php` according to the `blacklist_blocks()` example. Use your imagination—if something can mess things up, hide it!

## Patterns and reusable blocks of "small parts"

Make patterns or reusable blocks for difficult styling in Gutenberg—for example, special arrow buttons or columns with colored box backgrounds. Since these "small" things are often forgotten in technical documentation or planning, reflect on this and add them to the patterns task.
