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

Note: you must run `composer update` 

### Usage

The module has the ability to search the data,view data as grid-view and export the data. 

To create a report you must create class for Search  Model (`UserReport`)  ,  grid-view ( `UserReportGridView` )  and for Export  menu (`UserReportExportMenu` ).

##### Search model 

 This model is able to fetch its attributes, validation rules and filtering logic .

The data to be requested from the user will be represented by an `UserReport` model class as shown below.

```
use yii\base\Model;

class UserReport extends Model implements ReportInterface
{
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
            'facility_code' => 'Facility',
            'created_at_range' => 'Created At',
        ];
    }

}
```

The class extends from [[yii\base\Model]], a base class provided by Yii, commonly used to
represent form data.The class implements from [[codexten\yii\modules\report\reports\ReportInterface]].

The `UserReport` class contains three public members, `name` ,`phn_no` and `email`, which are used to store the data entered by the user.

