Admin Settings for Yii 2.0 +
============================
This package provide admin settings manager

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist codexten/yii-admin-settings:"^2.0.0"
```

or add

```json
"codexten/yii-admin-settings": "^2.0.0"
```

to the require section of your composer.json.


Configuration
-------------

```php

return \yii\helpers\ArrayHelper::merge(
    // other configurations
    [],
    // $adminSettings
    [
      'components' => [
            'adminSettings' => [
                
            ]  
        ]
    ]
    );

```