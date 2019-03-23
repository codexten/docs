# SMS

## Installation

To install, add the following to composer.json file

or add

```json
{
  "require": {
    ***
   "codexten/yii-sms": "~2.0"
  },
  "extra": {
    "config-plugin": {
      ***
      "???": [
        "$sms",
        "config/???.php"
      ]
  }
}
```

## params

```php

```

## Override Views



## Usage
```php

Yii::$app->sms->send($number)

```

## Links
 https://control.textlocal.in/docs/