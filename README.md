# A basic php coding standard

## file
* PHP 檔案內只能使用 `<?= ?>` 或 `<?php ?>`，__不要__使用 `<? ?>`
* 如果該檔是純 PHP 檔，省略結尾的 `?>`
* PHP 的縮排都使用__四個空格__
* 在所有檔案最下方留一行空行   
   
`<?= $frogyName ?>` 意同 `<?php echo $frogyName; ?>`

## class
* `namespace` & `use` 下面要空一行
* class 名稱採用__大寫開始的駝峰命名法__
* 宣告 class 的大括號 `{` 要在宣告的下一行
* 設定 property 一定要給 visibility: `public` or `private` or `protected`
```php
<?php
namespace app\controllers;

use vendro\components\BaseController;

class IndexController extends BaseController
{
    public $basePath = 'some/path';
    // ....
}
```

## function
* 宣告 function 一定要給 visibility: `public` or `private` or `protected`
* function 名稱採用__小寫開始的駝峰命名法__
* function 的各個變數以 `, ` 隔開，注意逗號後要空一格
* 宣告 function 的大括號 `{` 要在宣告的下一行
* function 結束的大括號 `}` 要在程式本體的下一行
```php
public function actionIndex($int1, $int2, $str = 'blabla')
{
    // ...
}
```

## parameter declaration
* 宣告變數時，變數名稱與值都要與 `=` 空一格
* 宣告陣列時，如果陣列過長可以換行並空四格後繼續給值
* 使用系統保留字時，都使用小寫
```php
$message = 'Hello Frogy';

$messagesA = ['H', 'e', 'l', 'l'];
$messageC = ['a'=>'A', 'b'=>'B'];
$messagesB = [
    0 => 'H',
    1 => 'e',
    2 => 'l',
    3 => 'l'
];

$sweat = true;
$conscience = false;
$yearEndBonus = null;
```

## control structures
* 控制結構如：`if`, `elseif`, `else`,`while`, `for`, `foreach`, `switch`
* 大括號開頭 `{` 與控制結構要同一行
* 控制結構與變數括號 `()` 及大括號 `{` 間都要空一格
* 控制結構結束的大括號 `}` 要在程式本體的下一行
```php
if ($access) {
    // ...
} elseif ($name = 'frogy') {
    // ...
} else {
    // ...
}

while ($hasMoney) {
    // ...
}

for ($i=0; $i<$max; $i++) {
    // ...
}

foreach ($posts as $index=>$post) {
    // ...
} 

switch ($target) {
    case 'Frogy':
        // ...
        break;
    case 'Frogyyyyyyy':
        // ...
        break;
    default:
        // ...
        break;
}
```

## Example
```php
<?php
namespace app\controllers\index;

use vendorA\helpers\ArrayHelper;
use vendorB\models\Post;
use vendroC\base\BaseController;

/**
 * app/controllers/index/IndexController.php
 * ...
 */
class IndexController extends BaseController
{
    /**
     * @var $name string ...
     */
    public $name = 'index_page';

    /**
     * This function is for ....
     * @param $id int ...
     * @return ...
     */
    public function actionIndex($id = 0)
    {
        if (empty($id)) {
            $post = new Post;
        } else {
            $post = Post::findOne($id);
        }

        return $this->render('view_index', [
            'post' => $post,
            'pageName' => $this->name
        ]);
    }
}

```
