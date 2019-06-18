Auth module for Yii 2.0 +
=========================
This Module provide basic authentication functionality such as registration,
login, forgotten password, otp verification, email verification ...

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist codexten/yii-sms:"^2.0.0"
```

or add

```json
"codexten/yii-sms": "^2.0.0"
```

to the require section of your composer.json.


Configuration
-------------

```php
// params.php
return \yii\helpers\ArrayHelper::merge(
    // other configurations
    [],
    // $sms
    [
        //sms
        'sms.defaultDriver' => 'textlocal',
    
        // textlocal
    
        //The email address used to log into Textlocal.
        'textlocal.username' => '',
        // visit https://control.textlocal.in/docs/ to get h
        'textlocal.hash' => '',
        'textlocal.sender' => '',
    
        // xpresssms
        'xpresssms.username' => '',
        'xpresssms.password' => '',
        'xpresssms.sender' => '',
    ]
    );

```

## customization
TBD