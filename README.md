Yii2 DataTables
===============

Yii2 Widget for [DataTables](https://github.com/DataTables/DataTables) plug-in for jQuery

## Installation

The preferred way to install this extension is through composer.

Either run

```
composer require "nullref/yii2-datatables" "*"
```
or add
```
"nullref/yii2-datatables": "*"
```
to the require section of your `composer.json` file.

## Server-side processing

To enable server-side processing add `DataTableAction` to controller like this:

```php
 class SomeController extends Controller
 {
     public function actions()
     {
         return [
             'datatables' => [
                 'class' => 'nullref\datatable\DataTableAction',
                 'modelClass' => 'app\models\Model',
             ],
         ];
     }
     
}
```

In DataTable options specify: 
```js
{
    "serverSide": true,
    "ajax": "/datatables"
}
```

## Add Links to row

```php
    <?= \nullref\datatable\DataTable::widget([
        'columns' => [
            //other columns
            [
                'class' => 'nullref\datatable\LinkColumn',
                'url' => ['/model/delete'],
                'options' => ['data-confirm' => 'Are you sure you want to delete this item?', 'data-method' => 'post'],
                'queryParams' => ['id'],
                'label' => 'Delete',
            ],
        ],
    ]) ?>
```

Properties of `LinkColumn`: 

- `label` - text placed in `a` tag;
- `url` - will be passed to `Url::to()`;
- `options` - HTML options of the `a` tag;
- `queryParams` - array of params added to `url`

