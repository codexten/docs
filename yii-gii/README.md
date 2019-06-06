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


Examples
--------

Country Module
```yml
# config/gii.yml
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

Geo Module
```yml
migration:
  create_province_table:
    fields: |
      country_id:integer:notNull:foreignKey(country),
      code:string(50),
      name:string(255),
      abbreviation:string(255)
model:
  province:
crud:
  province:
    modelClass: codexten\yii\modules\geo\models\Province

```
Commands
--------

To generate migration
```ssh

./vendor/bin/hidev gii yii-module-geo

```


## customization

TBD
