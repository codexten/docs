Gii
===

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
composer require --prefer-dist codexten/yii-gii:"^2.0.0"
```

or add

```json
"codexten/yii-gii": "^2.0.0"
```

to the require section of your composer.json.


Configuration
-------------

```yml
params:
  messageCategory: codexten:module:country
migration:
  create_country_table:
    fields: |
      code:string(50),
      is_enabled:boolean
model:
  country:
crud:
  country:
    modelClass: codexten\yii\modules\country\models\Country
```

## customization

TBD
