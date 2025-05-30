# Useful WP-CLI commands

### Regenerate all image thumbnails
`wp post list --post_type=attachment --post_mime_type=image --fields=ID --format=ids | xargs wp media regenerate`
