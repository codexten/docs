# Mailqueue

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist codexten/yii-mailqueue:"^2.0.0"
```

or add

```json
"codexten/yii-mailqueue": "^2.0.0"
```

to the require section of your composer.json.

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
