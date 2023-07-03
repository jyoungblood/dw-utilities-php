# DW Utilities (PHP)

### A collection of utility functions to facilitate an efficient workflow with the [Darkwave](https://github.com/hxgf/darkwave) web application toolkit.



# Installation
These functions are included with Darkwave, but they can be installed and used as standalone functions in any project.

Install the package with Composer:
```
composer require hxgf/dw-utilities
```

Then add it to your application:
```
use Darkwave\dw;
require __DIR__ . '/vendor/autoload.php';
```


# Available Methods


## dw::client_ip()
Returns the (best guess for the) current visitor's IP address, using a combination of 	`$_SERVER['HTTP_CLIENT_IP']`, `$_SERVER['HTTP_X_FORWARDED_FOR']`, and `$_SERVER['REMOTE_ADDR']`
```php
dw::client_ip();
```


## dw::authenticate()
Parses the JWT 'token' cookie and sets global authentication variables to be used by the rest of the application.
```php
dw::authenticate();
```


## dw::generate_jwt($user)
Uses [psr-jwt](https://github.com/RobDWaller/psr-jwt) to generate a JWT based on data from a given user's profile. Sets payload claims for `_id`, `name`, `avatar_url`, `screenname`, `admin_token`, and `staff_token`
```php
dw::generate_jwt($user);
```


## dw::convert_image($args)
Uses [php-image-resize](https://github.com/gumlet/php-image-resize) and [GD](https://www.php.net/manual/en/book.image.php) to convert a given image based on various configuration parameters.
```php
dw::convert_image([
  'source' => $_SERVER['DOCUMENT_ROOT'] . '/uploads/source-filename.jpg',
  'target' => $_SERVER['DOCUMENT_ROOT'] .  '/uploads/converted-filename.jpg',
  'resize' => [300, 300],
  // 'threshold' => 800
  'crop' => 'center',
  'quality' => 80
]);
```
