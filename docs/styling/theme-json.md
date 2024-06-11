# Theme.json in Ilme

Ilme uses theme.json for [global settings and styles](https://developer.wordpress.org/themes/global-settings-and-styles/) .

## Theme.json config

The file is structured into sections, Ilme uses the **settings** and **styles**-sections. Pattern styling through theme.json is optional. Ilme as now does not use customTemplates nor templateParts.
Observe that theme.json uses versioning, and is updated with newer Wordpress releases. From WP 6.6 onwards, the theme.jason uses v3. When updating Wordpress, check the [migration documentation](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-migrations/)

```
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {},
	"styles": {},
	"customTemplates": {},
	"templateParts": {},
	"patterns": []
}
```
