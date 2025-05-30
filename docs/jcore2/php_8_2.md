# Running Local Wordpress Container in PHP 8.2

The JCORE® WordPress container now defaults to PHP 8.2 so new projects will run that. If you want to run 8.2 in an
existing project run `jcore update` and set `image: 'jcodigi/wordpress:8.2'` in docker-compose.yml.
Currently Timber has so many deprecation notices (over 2000 per request) that the Deprecation notices had to be turned
off. If you want to turn on deprecation notices for testing purposes that is defined in a must-use plugin named
debug.php.

Change

```
error_reporting( E_ALL & ~E_DEPRECATED & ~E_USER_DEPRECATED );
```
to

```
error_reporting( E_ALL );
```

to enable deprecation notices.