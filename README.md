# Intervention Httpauth Class

Library to manage HTTP authentication with PHP. Made to work with **Laravel 4** but runs also standalone.


## Installation

You can install this Image class quick and easy with Composer.

Require the package via Composer in your `composer.json`.

    "intervention/httpauth": "dev-master"

Run Composer to update the new requirement.

    $ composer update

The Httpauth class is built to work with the Laravel 4 Framework. The integration is done in seconds.

Open your Laravel config file `config/app.php` and add the following lines.

In the `$providers` array add the service providers for this package.
    
    'providers' => array(

        ...

        'Intervention\Httpauth\HttpauthServiceProvider'

    ),
    

Add the facade of this package to the `$aliases` array.

    'aliases' => array(

        ...

        'Httpauth' => 'Intervention\Httpauth\Facades\Httpauth'

    ),

By default the authentication settings are fetched from `config/httpauth.php`. Please make sure to set your own options.

## Usage

* Image::__construct - Create new instance of Httpauth class
* Image::make - Creates new instance of Httpaccess with given config parameters
* Image::secure - Denies access for not-authenticated users

### Code example

```php
// create a new instance of Httpauth and call secure method
$auth = new Intervention\Httpauth\Httpauth;
$auth->secure();

// You can alter the user authentication settings at runtime 
$config = array('username' => 'admin', 'password' => '1234');
$auth = new Intervention\Httpauth\Httpauth($config);
$auth->secure();
```


### Code example (Laravel)

```php
// the most simple way to secure a url is to call the secure method from a route
Httpauth::secure();

// To setup user/password you can edit the config files or set a configuration at runtime
$config = array('username' => 'admin', 'password' => '1234');
Httpauth::make($config)->secure();
```
