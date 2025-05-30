# Whitelisting of Gutenberg Core blocks in JCORE®

## Why whitelisting?

To control what content the customer/user can add in the Guternberg-editor, JCOre hides by default all Core Guternberg blocks and only shows the ones whitelisted in 'blocks.php'. 

## A list of the basic blocks and their names whitelisted for the G-berg ediotor

```
$whitelisted_blocks = apply_filters(
		'jcore_whitelisted_gutenberg_blocks',
		array(
			'core/paragraph',
			'core/heading',
			'core/list',
			'core/list-item',
			'core/image',
			'core/quote',
			'core/separator',
			'core/shortcode',
			'core/spacer',
			'core/cover',
			'core/file',
			'core/video',
			'core/table',
			'core/html',
			'core/preformatted',
			'core/button',
			'core/buttons',
			'core/group',
			'core/spacer',
			'core/block',
			'wp-bootstrap-blocks/column',
			'wp-bootstrap-blocks/container',
			'wp-bootstrap-blocks/row',
			'gravityforms/form',
		)
	);
```

## To add more blocks in your child theme, use this filter in your theme functions-file: 
```
add_filter(
	'jcore_whitelisted_gutenberg_blocks',
	function( $blocks ) {
		$blocks[] = 'core/post-title';
		$blocks[] = 'core/post-date';
		$blocks[] = 'core/pullquote';
		$blocks[] = 'core/quote';
		$blocks[] = 'core/media-text';
		return $blocks;
	}
);
```
