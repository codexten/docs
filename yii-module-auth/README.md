Auth module for Yii 2.0 +
=========================
This Module provide basic authentication functionality such as registration,
login, forgotten password, otp verification, email verification ...

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist codexten/yii-module-auth:"^2.0.0"
```

or add

```json
"codexten/yii-module-auth": "^2.0.0"
```

to the require section of your composer.json.


Configuration
-------------

```php

return \yii\helpers\ArrayHelper::merge(
    // other configurations
    [],
    // $moduleAuth
    [
        'modules' => [
            'auth' => [
                'enableRegistration' => true,
                'enableAutoLoginAfterRegistration' => true,
                 'enablePasswordRecovery' => false,
                'controllerMap' => [
                    'phone-number-verification' => [
                        'modelClass' => PhoneNumberVerificationForm::class,
                    ],
                    'email-verification' => [
                        'modelClass' => EmailVerificationForm::class,
                    ],
                ],
            ],
        ],
        'as globalAccess' => [
            'class' => '\codexten\yii\behaviors\GlobalAccessBehavior',
            'rules' => [
                [
                    'controllers' => ['site'],
                    'allow' => true,
                    'roles' => ['?'],
                    'verbs' => ['GET'],
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
        'container' => [
            'definitions' => [
                // forms
                \codexten\yii\modules\auth\models\RegistrationForm::class => [
                    'class' => RegistrationForm::class,
                ],
                \codexten\yii\modules\auth\models\LoginForm::class => [
                    'class' => LoginForm::class,
                ],
                
                //actions
                AccountLoginAction::class => [
                    'class' => AccountLoginAction::class,
                    'layout' => null,
                ],
            ],
        ],
    ]
    );

```

## customization

### extend registration
TBD
### extend Login Form
TBD
### SMS otp verification
TBD
