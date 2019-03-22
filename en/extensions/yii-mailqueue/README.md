# Mailqueue

## Installation

To install, add the following to composer.json file

or add

```json
{
  "require": {
    ***
   "codexten/yii-mailqueue": "~2.0"
  }
}
```

## params

```php
return [
    // default mailer
    'mailer' => 'gmail',
    
    //gmail
    'gmail.username' => '',
    'gmail.password' => '',
];

```

## commands

```ssh
./vendor/bin/hidev mailqueue
```


## Usage
