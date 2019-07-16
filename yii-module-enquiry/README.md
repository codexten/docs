Enquiry module for Yii 2.0 +
=========================

## Creating Module

#### Configurations

core.php

```
return [
    'aliases' => [
        '@moduleEnquiry' => '@codexten/yii/modules/enquiry',
    ],
];
```



moduleEnquiry.php

```
return [
    'modules' => [
        'enquiry' => [
            'class' => Module::class,
            'viewPath' => '@moduleEnquiry/views',
            'controllerNamespace' => 'codexten\yii\modules\enquiry\controllers',
            'controllerMap' => [
                'enquiry' => [
                    'class' => CrudController::class,
                    'modelClass' => Enquiry::class,
                ],
            ],
        ],
    ],
];
```



add to composer.json

```
"config-plugin": {
  "core": "config/core.php",
  "moduleEnquiry": "config/moduleEnquiry.php",
  "migrationNamespaces": "config/migrationNamespaces.php"
}
```



Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist codexten/yii-module-enquiry:"^2.0.0"
```

or add

```json
 "codexten/yii-module-enquiry": "~2.0.0",
```

to the require section of your composer.json.



Add  $moduleEnquiry to admin and site  of your composer.json.

```json
"config-plugin": {
  "admin": [
    "$moduleEnquiry",
  ],
  "site": [
    "$moduleEnquiry",
  ]
}
```

Configuration
-------------

admin config

```php

return \yii\helpers\ArrayHelper::merge(
    // other configurations
    [],
   // $moduleEnquiry
    [
        'modules' => [
            'enquiry' => [
                'controllerMap' => [
                    'enquiry' => [
                        'enabledActions' => [
                            'index',
                            'view',
                            'delete',
                        ],

                    ],
                ],
            ],
        ],
    ]
    );

```

site config

```php
return \yii\helpers\ArrayHelper::merge(
    // other configurations
    [],
    // $moduleEnquiry
    [
        'components' => [
            'urlManager' => [
                'rules' => [
                    '/contact-us' => '/enquiry/enquiry/create',
                ],
            ],
            'view' => [
                'theme' => [
                    'pathMap' => [
                        '@moduleEnquiry/views' => [
                            '@gnt/site/modules/enquiry/views',
                        ],
                    ],
                ],
            ],
        ],
        'modules' => [
            'enquiry' => [
                'controllerMap' => [
                    'enquiry' => [
                        'enabledActions' => [
                            'create',
                        ],
                    ],
                ],
            ],
        ],
    ]
  );
```

## Override Views

path of create.php

​	site->modules->enquiry->views->enquiry->create

```php
<?php $form = ActiveForm::begin() ?>

<?= $this->render('form/_fields', ['model' => $model, 'form' => $form]) ?>

<div class="form-group">

    <?= Html::submitButton('Send', ['class' => 'btn btn-primary']) ?>

</div>

<?php ActiveForm::end() ?>
```

## customization

TBD
