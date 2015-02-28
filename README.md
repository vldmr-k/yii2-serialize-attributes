# yii2-serialize-attributes

Install
```
require : {
  "wowkaster/yii2-serialize-attributes": "dev-master"
}
```

Hot to use.
```
class SomeModel extends \yii\db\ActiveRecord {
  public functuin rules() {
    return [
      [['options'], 'safe']
    ];
  }
  
  ....
  
  public function behaviors() {
    return [
        [
            'class' => SerializeAttributesBehavior::className(),
            'convertAttr' => ['options' => 'json']
        ]
    ];
  }
  
  ====// OR //====
  public function behaviors() {
    return [
        [
            'class' => SerializeAttributesBehavior::className(),
            'convertAttr' => ['options' => 'serialize']
        ]
    ];
  }
}


$model = new SomeModel();
$model->options = ['value1', 'value2', 'param' => 'value'];
$model->save();

print_r($model->options); => Array('value1', 'value2', 'param' => 'value')

$model = SomeModel::findOne(1);
print_r($model->options); => Array('value1', 'value2', 'param' => 'value')

```
