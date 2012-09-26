# phpass - Laravel bundle

*phpass* is a portable public domain password hashing framework from the [Openwall Project]
(http://www.openwall.com/phpass/) packaged as a bundle for the [Laravel PHP Framework](https://github.com/laravel/laravel).  

It uses the OpenBSD-style Blowfish-based bcrypt (*CRYPT_BLOWFISH*). Fallback includes BSDI-style extended DES-based hashes (*CRYPT_EXT_DES*) and 
MD5-based salted and variable iteration count password hashes implemented in phpass itself.

-----

## Installation

Use Artisan to install *phpass*:

```bash
php artisan bundle:install phpass
```

Enable it by adding the following to your `bundles.php` file:

```php
return array(
  'phpass' => array('auto' => true),
)
```

## Usage

Initiate the phpass class:

```php
/**
 *
 * @param   int			base-2 logarithm of the iteration count used for password stretching (default is 8);
 * @param	boolean		use portable hashes (default is FALSE);
 *
 * Omitting parameters assumes default values, which should be fine in most cases.
 *
 */

$do = new phpass;
```

Hash password:

```php
$password = 'your extremely secure password';
$hashedPassword = $do->HashPassword($password);
```

Check password against the hash:

```php
$hashedPassword = '$2a$08$aZtg0P47YOrdAh/fPARzDuBaAJMhu4ueeri8Hxh6OOAjI80HXVwHu';
$password = 'your extremely weak password';
echo ($do->CheckPassword($password, $hashedPassword)) ? 'Correct!' : 'Wrong!'; 
```

## Miscellaneous

Visit the [Openwall Project](http://www.openwall.com/phpass/) for more information on this class and password security in general.