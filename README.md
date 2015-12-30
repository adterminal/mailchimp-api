MailChimp API
=============

Simplest MailChimp API v3 wrapper, in PHP.

This lets you get from the MailChimp API docs to the code as directly as possible.

Requires PHP 5.3 and a pulse. Abstraction is for chimps.

Installation
------------

You can install mailchimp-api v3 dev branch using Composer:

```
composer require adterminal/mailchimp-api:dev-master
```

You will then need to:
* run ``composer install`` to get these dependencies added to your vendor directory
* add the autoloader to your application with this line: ``require("vendor/autoload.php")``

Alternatively you can just download the MailChimp.php file and include it manually:

```php
include('./Mailchimp.php');
```

Examples
--------

List all the mailing lists (`lists` method)

```php
use \Adterminal\MailChimp\MailChimp;

$MailChimp = new MailChimp('abc123abc123abc123abc123abc123-us1');
print_r($MailChimp->get('lists'));
```

Subscribe someone to a list and an interest group

```php
use \Adterminal\MailChimp\MailChimp;

$MailChimp = new MailChimp('abc123abc123abc123abc123abc123-us1');
$result = $MailChimp->post('lists/b1234346/members', array(
				'email_address'     => 'davy@example.com',
				'status'			=> 'subscribed',
				'merge_fields'      => array('FNAME'=>'Davy', 'LNAME'=>'Jones'),
				'interests' 		=> array( '2s3a384h' => true )
			));
print_r($result);
```
