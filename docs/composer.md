# Composer

Composer is a package manager for PHP packages, and can be used to install WP plugins as well as libraries needed for JCORE®. Composer is used in different degrees in different projects. Sometimes it is only used to install Timber and ACF, and sometimes to manage all plugins in the project.

# Plugins & Packages required in JCORE (the starter set)

Plugins that are always part of the JCORE base setup and what they do. The list will in most cases be extended on a project basis.

```json
"timber/timber":
```

Drives the whole Twig theme template structure.

```json
"jco/advanced-custom-fields-pro":
```

Adds the custom fields (to block and theme)

```json
"jco/wp-migrate-db-pro":
```

WP db migration plugin. Can be used in publication for database changes.

```json
"wpackagist-plugin/better-search-replace":
```

A lighter option for database changes than wp-migrate-db-pro.

```json
"sentry/sentry":
```

Sentry is a crash reporting platform that provides you with real-time insight into production deployments with info to reproduce and fix crashes.

```json
"symfony/http-client":
```

Standalone PHP library providing a specific feature, which can be used in any PHP application.

```json
"wpackagist-plugin/wordpress-seo":
```

Yoast - for SEO and social media.

```json
"nyholm/psr7":
```

A fast PHP7 implementation of PSR-7. Required by symfony.

```json
"wpackagist-plugin/wp-bootstrap-blocks":
```

Adds functioning columns with media queries. (Do not use the columns-block native to Gutenberg. Responsivity is lacking, or add media queries yourself.)

```json
"wpackagist-plugin/redirection":
```

To redirect URLs from the WP backend.

```json
"jco/minimal-coming-soon-maintenance-mode":
```

Plugin for coming soon pages.

```json
"jco/webtoffee-gdpr-cookie-consent":
```

Webtoffee gdpr popup

```json
"jco/gravityforms":
```

For form handling.

```json
"jco/polylang-pro":
```

For multilingual sites.

```json
"wpackagist-plugin/mailgun":
```

An email automation engine for configuration and routing.

### Development Plugins & Packages

These plugins are only in use in development environment via `require-dev` in composer.

```json
"wpackagist-plugin/pattern-manager":
```

Easily create and manage block patterns in the backend that are automatically saved as php.

```json
"wpackagist-plugin/loco-translate":
```

Create string translations locally for pushing to git.

```json
"squizlabs/php_codesniffer": "^3.7",
"dealerdirect/phpcodesniffer-composer-installer": "^1.0",
"wp-coding-standards/wpcs": "dev-develop",
```

These three packages are used for setting up [WordPress Coding Standards for PHP_CodeSniffer](https://github.com/WordPress/WordPress-Coding-Standards) in the project.

## Languages and translations

JCORE adds Loco Translate locally, and the theme/languages folder contains a jcore.pot file. The project's "small words" are translated (for example on a Swedish site) in development, and the plugin should not be added to Composer. Translations are pushed with the project.

```json
"wpackagist-plugin/loco-translate":
```

- Only move to require from require-dev in Composer if the CUSTOMER themself needs access and does translations.
- Then Loco Translate needs to be added to Composer, activated and a CUSTOM translation added on live, for it not to be overwritten by push.
