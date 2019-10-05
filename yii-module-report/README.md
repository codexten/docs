# yii-module-report

yii-module-report is a report creation module ,that handles common tasks such as search, grid-view and export generation.

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
$ php composer require codexten/yii-module-report "~2.0.0"
```

or add

```
"codexten/yii-module-report": "~2.0.0"
```

to the `require` section of your `composer.json` file.

### Configure

Add 

```
"config-plugin": {
"admin":[
 "$moduleReport",
 "config/admin.php"
	]
}
```

in  `composer.json` file.



Go To:

​		config->admin.php





```
use codexten\yii\modules\report\controllers\ReportController;

[   
	'modules' => [      
		'report' => [     
			'viewPath' => '@tms/sourcing/admin/modules/report/views',  
            //set the  path accordingly
			'controllerMap' => [        
				'tr' => [          
						'class' => ReportController::class,           
						'reportClass' => UserReport::class,              
						'gridViewClass' => UserReportGridView::class,           
						'exportMenuClass' => UserReportExportMenu::class,         
				],          
			],    
		],   
	],  
	'components' => [
            'view' => [
                'theme' => [
                    'pathMap' => [
                        '@moduleReport/views' => [
                            '@tms/sourcing/admin/modules/report/views',
                           //set the  path accordingly
                        ],
                    ],
                ],
            ],
        ],
]
```



### Usage

The module has the ability to search the data,view data as grid-view and export the data. 

To create a report you must create class for Search  Model (`UserReport`)  , for  grid-view ( `UserReportGridView` )  and for Export  menu (`UserReportExportMenu` ).



##### Search model 

 This model is able to fetch its attributes, validation rules and filtering logic .

The data to be requested from the user will be represented by an `UserReport` model class as shown below.

```
use yii\base\Model;
use codexten\yii\modules\report\reports\ReportInterface;
use codexten\yii\modules\report\reports\ReportTrait;use codexten\tms\sourcing\core\helpers\BroadcastHelper;
use codexten\tms\sourcing\core\models\Broadcast;

class UserReport extends Model implements ReportInterface
{
	use ReportTrait;
 	
 	public $name;
 	public $phn_no;
	public $email;
	
	//validation rules
	public function rules()
    {
        return [
            [
                [
                    'name',
                    'phn_no',
                    'email',
                ],
                'safe',
            ],
        ];
    }
    
    //labels for attributes
     public function attributeLabels()
    {
        return [
            'name' => 'Name',
            'phn_no' => 'Phone Number',
            'email'  => 'Email',
        ];
    }
    
    //To get the base query
     protected function getBaseQuery()
    {
        $query = User::find()
            ->alias('user')
            //->distinct('user.id')
            //->joinWith('broadcast as broadcast');
		    // set accordingly
		    
        return $query;
    }
	
	//...
}
```

The `UserReport` class extends from [[yii\base\Model]], a base class provided by Yii, commonly used to
represent form data.

The `UserReport` class implements from [[codexten\yii\modules\report\reports\ReportInterface]].

The `UserReport` class contains three public members, `name` ,`phn_no` and `email`, which are used to store the data entered by the user.

Trait `ReportTrait` is extended from  [[codexten\yii\modules\report\reports\ReportTrait]].

In `getBaseQuery()` function, model `User` is extended from iteself.

Also set view page for the Search model class accordingly.

##### GridView Class

The GridView widget is used to display data in a grid. It provides features like [sorting](https://www.yiiframework.com/doc/api/2.0/yii-widgets-baselistview#$sorter-detail), [paging](https://www.yiiframework.com/doc/api/2.0/yii-widgets-baselistview#$pager-detail) and also [filtering](https://www.yiiframework.com/doc/api/2.0/yii-grid-gridview#$filterModel-detail) the data.

```
use codexten\yii\dataView\widgets\GridView;

class UserReportGridView extends GridView
{
	use UserReportGridViewTrait;
}
```

The `UserReportGridView` class extends from [[codexten\yii\dataView\widgets\GridView]] 

A Trait is similar to a class.

The `UserReportGridView` class uses the Trait  `UserReportGridViewTrait` 

```
use codexten\yii\helpers\ArrayHelper;
use yii\grid\SerialColumn;

trait UserReportGridViewTrait
{    
	public function columns()
    {
        return ArrayHelper::merge(
            parent::columns(),
            [
                'sl' => [
                    'class' => SerialColumn::class,
                ],
                'name',
                'phn_no',
                'email',
            ]
        );
    }
    
}
```

##### ExportMenu Class

Export menu class is used to export data in various formats (e.g. excel, html, pdf, csv etc.) it just displays the export actions in form of a ButtonDropdown menu



```
use codexten\yii\dataView\grid\export\ExportMenu;

class UserReportExportMenu extends ExportMenu
{
	use UserReportGridViewTrait;   	
}
```

The class extends from [[codexten\yii\dataView\grid\export\ExportMenu]] 

