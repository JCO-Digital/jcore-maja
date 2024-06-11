# Theme.json in Ilme

Ilme uses theme.json for [global settings and styles](https://developer.wordpress.org/themes/global-settings-and-styles/) .

## Theme.json config

The file is structured into sections, Ilme uses the **settings** and **styles**-sections. Pattern styling through theme.json is optional. Ilme as now does not use customTemplates nor templateParts.
Observe that theme.json uses versioning, and is updated with newer Wordpress releases. From WP 6.6 on-wards, the theme.json uses v3. When updating Wordpress, check the [migration documentation](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-migrations/)

```
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 3,
	"settings": {},
	"styles": {},
	"customTemplates": {},
	"templateParts": {},
	"patterns": []
}
```

## Theme settings

The settings that were included in Jcore2 varaibles can now be set in theme.json:

- Theme colors (as many as needed)
- Responsive breakpoints and spacing
- Page layout dimensions, 2 different, normal and wide content.
- All typography
- Blocks: An object for configuring per-core-block settings, like image, pullquote etc.

## Theme styles

The theme styles sets the settings onto the G-berg content:

- Text and background color
- Paragraph font-size and line-height
- Headings font-size, headings font-family
- G-berg group padding
- Link color

The presets (settings) are applied in the styles-section with a special syntax:
var:preset|$feature|$slug. So base color in this instance would be var:preset|color|base. For custom color "success" use
==var:custom|color|success==.
