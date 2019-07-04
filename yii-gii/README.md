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

### CRUD GENERATION

- CRUD stands for create-read-update-delete

  - In gii.yml  file 

    ```
    crud:
      customer_group:
        modelClass: codexten\ecommerce\core\models\CustomerGroup
        namespace: codexten\ecommerce\admin\
    ```

  - Run the command in Terminal

    `./vendor/bin/hidev gii/crud packagename `

- CustomerGroup controller will be created automatically in the location ecommerce->src->admin->controllers

  CustomerGroupController.php

  ```
  namespace codexten\ecommerce\admin\controllers;
  
  use Yii;
  use codexten\ecommerce\core\models\CustomerGroup;
  use codexten\yii\web\CrudController;
  
  class CustomerGroupController extends CrudController
  {
      public $modelClass = CustomerGroup::class;
  
      public function actions()
      {
          $actions = parent::actions();
  
          return $actions;
      }
  
  }
  ```

- _form.php, create.php, update.php, index.php, view.php will be created automatically in the location ecommerce->src->admin->views->customer_group

  

_form.php file

```
use codexten\ecommerce\core\models\CustomerGroup;
use yii\bootstrap\ActiveForm;
use yii\helpers\Html;

/* @var $this yii\web\View */
/* @var $model CustomerGroup */
?>

<div class="row">
    <div class="col-md-6">

    <?php $form = ActiveForm::begin() ?>

        <?= $form->field($model, 'code') ?>

        <?= $form->field($model, 'name') ?>

        <div class="form-group">

            <?= Html::submitButton(
                $model->isNewRecord ? Yii::t('codexten:module:core', 'Create') : Yii::t('codexten:module:core', 'Update'),
                ['class' => $model->isNewRecord ? 'btn btn-success' : 'btn btn-primary']) ?>

        </div>

        <?php ActiveForm::end() ?>

    </div>
</div>
```



index.php file 		

```
<?php

use codexten\yii\web\widgets\IndexPage;
use yii\grid\GridView;

/* @var $this yii\web\View */
/* @var $dataProvider yii\data\ActiveDataProvider */
/* @var $searchModel  */

$this->title = Yii::t('codexten:module:core', 'Customer Groups');
?>

<?php $page = IndexPage::begin([
    'title' => $this->title,
]) ?>

<?php $page->beginContent('main-actions') ?>

<?= $page->renderButton('create', ['create'], ['class' => ['btn-success']]) ?>

<?php $page->endContent() ?>

<?php $page->beginContent('table') ?>

<?= GridView::widget([
    'dataProvider' => $dataProvider,
    'filterModel' => $searchModel,
    'columns' => [
        'code',
        'name',
        [
            'class' => 'yii\grid\ActionColumn',
            'options' => ['style' => 'width: 5%'],
            'template' => '{update} {delete}',
        ],
    ],
]); ?>

<?php $page->endContent() ?>

<?php $page->end() ?>
```



update.php file	

```
use codexten\yii\web\widgets\UpdatePage;

/* @var $this yii\web\View */
/* @var $model codexten\ecommerce\core\models\CustomerGroup */

$this->title = Yii::t('codexten:module:core', 'Update Customer Group: ' . $model->name, [
    'nameAttribute' => '' . $model->name,
]);
?>
<?php $page = UpdatePage::begin() ?>

<?php $page->beginContent('form') ?>

<?= $this->render('_form', ['model' => $model]) ?>

<?php $page->endContent() ?>

<?php $page->end() ?>
```

​	

create.php file

```
<?php

use codexten\yii\web\widgets\CreatePage;


/* @var $this yii\web\View */

$this->title = Yii::t('codexten:module:core', 'Create Customer Group');
?>
<?php $page = CreatePage::begin() ?>

<?php $page->beginContent('form') ?>

<?= $this->render('_form', ['model' => $model]) ?>

<?php $page->endContent() ?>

<?php $page->end() ?>
```

​	