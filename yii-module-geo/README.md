Geo module for Yii 2.0 +
=========================

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist codexten/yii-module-geo:"^2.0.0"
```

or add

```json
"codexten/yii-module-geo": "^2.0.0"
```

to the require section of your composer.json.

Menu Items
----------

```php
    [
        'label' => 'Countries',
        'icon' => 'flag',
        'url' => ['/country/country/index'],
        'active' => controllerId() == 'country',
    ],
    [
        'label' => 'Province',
        'icon' => 'list',
        'url' => ['/geo/province/index'],
        'active' => controllerId() == 'provience',
    ],
    [
        'label' => 'Zones',
        'icon' => 'list',
        'url' => ['/geo/zone/index'],
        'active' => controllerId() == 'zone',
    ],
```


Configuration
-------------

```php

return \yii\helpers\ArrayHelper::merge(
    // other configurations
    [],
    // $moduleGeo
    [
       
    ]
    );

```

## customization

TBD
