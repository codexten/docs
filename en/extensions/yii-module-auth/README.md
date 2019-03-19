# Auth Module

## Installation

To install, add the following to composer.json file

or add

```json
{
  "require": {
    ***
   "codexten/yii-module-auth": "~2.0"
  },
  "extra": {
    "config-plugin": {
      ***
      "???": [
        "$moduleAuth",
        "config/???.php"
      ]
  }
}
}

```

## Configurations Override 

```php
 // auth module
    [
        'modules' => [
            'auth' => [
                'enableRegistration' => true,
            ],
        ],
        'as globalAccess' => [
            'class' => '\codexten\yii\behaviors\GlobalAccessBehavior',
            'rules' => [
                [
                    'controllers' => ['site', 'setup-data'],
                    'allow' => true,
                    'roles' => ['?', '@'],
                ],
                [
                    'allow' => true,
                    'roles' => ['user'],
                ],
            ],
        ],
        'components' => [
            'view' => [
                'theme' => [
                    'pathMap' => [
                        '@codexten/yii/modules/auth/' => [
                            '@site/modules/auth/',
                        ],
                    ],
                ],
            ],
        ],
    ]

```

## Override Views



## Usage
