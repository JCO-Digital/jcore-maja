# JCOre theme base styling

An example of a base style set workflow for a JCOre base project.

A more elaborate detailed list of tasks can be found in google docs https://docs.google.com/document/d/1jPw7kSgcva80eQd3EZF-G2tEF2dhRTpEEbCJ5Djn6ac/edit?usp=sharing

## Mock up and stylesheet

Ask for mock up and stylesheet in dev mode and check mock up has grid mode too.

If no style sheet is available, do not start working on styles. Look through the whole mock up and stylesheet. Look for the most common colors/styles/theme/rounded corner, and let the most common style be the primary/default/main style.
Check that colors are sufficient, as added in the previous step. If not, more colors can be added in functions.php 'jcore_customizer_colors'.

## Colors

Theme colors are defined in the WP customizer (backend). You can reference colors in SCSS using bootstarp variables. For example $primary becomes `color: var(--bs-primary)` and so on.

If you need to add more colors to the list you can add new variables to the list: $theme-colors in \_colors.scss. These new colors have to be added also to jcore_customizer_colors filter in function.php. Use matching variable names as in the \_colors.scss.

## Fonts

If Google fonts, add the sizes that are present in the style sheet and the italics version of these. (Most changes related to fonts can be found in the variables and the typography style sheets).

- Insert sizes in variables.scss

- Decide upon a small and large font size that corresponds to a size needed.

- Insert heading-sizes in variables.scss

- Check that the responsive scaling settings if $enable-rfs: true;

- Make an example, and see how the responsive scaling affects the heading sizing. Adjust with bespoke media queries, if necessary.

### Line height

Check separately for headings, as the larger the font size, the smaller the spacing needs to be for a good look. Make examples of headings that span several lines.

### Font weight

Check from mock up, add to typography stylesheet.

### Letter-spacing

Add letter spacing to the typography stylesheet.

### Margin bottom

Set margin bottom for all headings and for the paragraph, not to forget list and link items, in the typography stylesheet. In single.css there are ready set margin-bottom for headings. Unify/remove from single. It is better all base font styling is in the typography stylesheet.

## Check container widths

Check container widths on mock up with the grid visible. Decide on narrow and wide container widths, and adjust grid breakpoints if necessary. Set group paddings to smaller/wider, depending on the general mock up look. -All in variables. Set all paddings and margins with the $spacer unit.

## Text links and their colors/behavior.

Base styles can be found last in variables.scss . Additional styling, like hover effects etc should be added to typography.

## Buttons (\_buttons.scss) will be refactored in grasshopper with a bespoke jcore buttons-block.

Button styling is done both for twig/code use in “simple” form, and Gutenberg use in the “more complicated form”. For easier styling, different classes can be used for styling in G-berg and theme code. If the same classes are used, the negated btn style is needed.

Special link styles are also added as buttons, even if the look is more like a text link with an animated arrow to the right/left. All these are added to the buttons.scss.

## List styling.

Check that list base styles exist, have margin and decent spacing. If in the stylesheet, add bullet points as in stylesheet. If very special lists exist, add them as blocks with ACF repeater fields. If only the bullet list is present in the stylesheet, also check that the numbered list works “in the same way”, equal inline-start-padding and equal spacing. The inline-start-style can be found in \_content.scss

## Quotes.

Styles from stylesheet go into gutenberg.scss, as G-berg uses quote and pullquote. Test these in G-berg. -Come up with your own solution for the pullquote, or blacklist pullquote in functions.php.

## Responsive JCOre spacers (first in gutenberg.scss).

Adjust to fit your theme. They work on mobile with the value set in G-berg and on desktop with the media query value.

## Images.

Border-radius/shadows/layers/spacing in text. Set in G-berg and beware G-berg images come in many divs.. "figure", "img'' etc. Check every image-type inserted and its divs.

## Box-elements in Gutenberg

Check the mock up for boxed content in G-berg. Coloring, border-radius, and add classes as needed to \_gutenberg.scss.

## Site-spanning background/front page background.

Site-spanning background images can be added to the theme in customizer. For special effects/color layers, the layout twig file might need cp to child and modified.

## Check the WP login view

What color scheme? If no mock up, make reasonable choices! Add to variables: $login-bg, $login-form, $login-color. Button styles might affect the show password eye so make sure to check that it is not broken.

## Footer

Special link/list/color styling and widget areas. Social media icons. -It is polite to the person coding the footer, to check how the styling in the footer is different from the general color theme/list/link styles. Possibly make the footer exceptions already at this stage in footer.scss, ex. different list/link styling/coloring. (This because now it is all fresh in mind, and you will know what to overwrite, and how to achieve the new style with least effort. )

## Assets/logo svg's

Check that all assets/logos are available for special styling/imagery/decorative elements.

## TEST

All typography on a G-berg basic page. Lorem ipsum, all headings, paragraph of text, lists(ul and ol), inline links, buttons and their spacings. Also the responsive behaviors of all these in mobile view/iPAd view. Some variables might need adjusting. It is all right to ask the AD or suggest changes. Nobody's perfect!

## Document

In Code, WP-ohjeet or Dev-notes the classes needed in G-berg/code to achieve special styling.

## Core G-berg Blocks

Go through what G-berg base blocks are actually needed in the project, and blacklist the ones that are not allowed/not used in mock up in functions.php according to blacklist_blocks() example. Use your imagination. -What can eff things up -> HIDE it!

## Patterns and reusable blocks of "small parts"

Make patterns or reusable blocks of difficult styling in G-berg -For ex. special arrow buttons or columns with colored box backgrounds etc.
Because these "small" things are often forgotten from the technical documentation/planning, maybe here, reflect over this, and add to patterns-task?
