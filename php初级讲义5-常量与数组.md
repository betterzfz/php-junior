#### 常量的定义
常量是相对于变量来说的，常量名由字母数字下划线构成且不能以数字开头，与变量不同，常量不需要使用`$`作为牵引，在脚本的生命周期中，常量的值是不可以发生变化的。常量名区分大小写，通常会用大写字母命名常量。

#### 常量的语法
```php
define('title', 'this is a title');
echo title.'<br/>'; // this is a title
define('TITLE', 'THIS IS A TITLE');
echo TITLE.'<br/>'; // THIS IS A TITLE
define('TITLE', 'TITLE');
echo TITLE.'<br/>'; // THIS IS A TITLE
// TITLE = 'TITLE'; // 网页无法正常运作
define('Title', 'Title');
echo Title.'<br/>'; // Title
define('_title', '_title');
echo _title.'<br/>'; // _title
define('title1', 'title1');
echo title1.'<br/>'; // title1
define('1_title', '1_title');
// echo 1_title.'<br/>'; // 网页无法正常运作
const hello = 'hello, world';
echo hello.'<br/>'; // hello, world
const hello = 'hello, shanghai';
echo hello.'<br/>'; // hello, world
// hello = 'hello, shanghai'; // 网页无法正常运作
// unset(hello); // 网页无法正常运作
var_dump($hello); // NULL
echo '<br/>'; 
$hello = 'hello, beijing';
echo $hello.'<br/>'; // hello, beijing
unset($hello); // unset()函数用来释放指定的变量
var_dump($hello); // NULL
echo '<br/>';
echo '<pre>';
print_r(get_defined_constants()); // 打印出已经定义的常量列表
echo '</pre>';
```

#### 常量的说明
* 常量可以使用函数`define()`或关键字`const`来定义，在`php5.3.0`之前的版本中关键字`const`只能用来定义类常量。
* 常量不可以被销毁。
* 常量只能包含简单值，即常量应该仅包含标量数据，包括整形，布尔型，字符串型和浮点型。
* 如果使用了一个未定义的常量，则会报一个未定义常量的`Notice`错误，同时将使用的常量名作为常量值。如果使用了一个未定义的变量将得到`NULL`。
```php
ini_set('display_errors', 'on');
error_reporting(E_ALL);
echo world.'<br/>'; 
// Notice: Use of undefined constant world - assumed 'world' in /Library/WebServer/Documents/index.php on line 4
// world
const TITLE = 'this is a title';
echo Title.'<br/>';
// Notice: Use of undefined constant Title - assumed 'Title' in /Library/WebServer/Documents/index.php on line 8
// Title
```

#### 数组的定义
数组是一系列键值对的组合，键和值组成了数组的一个元素，元素之间用逗号隔开，键表示了元素的索引，值表示了元素的具体数据。数组的键可能是数字或字符串，值可以是任意合法的数据。

#### 数组的语法
```php
$four_king = array('刘德华', '张学友', '黎明', '郭富城');
echo $four_king.'<br/>'; // Array
print_r($four_king); // Array ( [0] => 刘德华 [1] => 张学友 [2] => 黎明 [3] => 郭富城 )
echo '<pre>';
print_r($four_king);
echo '</pre>';
/*Array
(
    [0] => 刘德华
    [1] => 张学友
    [2] => 黎明
    [3] => 郭富城
)*/
echo '<pre>';
var_dump($four_king);
echo '</pre>';
/*array(4) {
    [0]=>
    string(9) "刘德华"
    [1]=>
    string(9) "张学友"
    [2]=>
    string(6) "黎明"
    [3]=>
    string(9) "郭富城"
}*/
// []为短数组定义语法 自php5.4起支持
$four_king = ['刘德华', '张学友', '黎明', '郭富城']; // 索引数组 索引默认从0开始 依次加1
print_r($four_king); // Array ( [0] => 刘德华 [1] => 张学友 [2] => 黎明 [3] => 郭富城 )
echo '<br/>';
$four_king = [1 => '刘德华', 3 => '张学友', '黎明', '郭富城']; // 可以指定索引数组的键 后面没有制定的键以前一个键为基加1
print_r($four_king).'<br/>'; // Array ( [1] => 刘德华 [3] => 张学友 [4] => 黎明 [5] => 郭富城 )
echo '<br/>';
$four_king = ['andy' => '刘德华', 'Jacky' => '张学友', 'Leon' => '黎明', 'Aaron' => '郭富城']; // 关联数组
print_r($four_king).'<br/>'; // Array ( [andy] => 刘德华 [Jacky] => 张学友 [Leon] => 黎明 [Aaron] => 郭富城 ) 
echo '<br/>';
$four_king = ['andy' => '刘德华', 'Jacky' => '张学友', '黎明', '郭富城']; // 关联数组
print_r($four_king).'<br/>'; // Array ( [andy] => 刘德华 [Jacky] => 张学友 [0] => 黎明 [1] => 郭富城 ) 
echo '<br/>';
```

#### 数组的说明
* 数组可分为一维数组和多维数组，当数组元素的值为一个数组时，该数组即为多维数组。
* 数组可分为用数字做键的索引数组，用字符串做键的关联数组以及混合了数字和字符串键的混合数组，这仅仅是人为的划分方便使用，`php`本身不做这样的区分。
* 如果数组元素的键是一个包含了合法整型值的字符串，则键会被转换成整形，如：
```php
$arr = ['12' => 'tony', '14' => 'tom'];
echo '<pre>';
var_dump($arr);
echo '</pre>';
/*array(2) {
    [12]=>
    string(4) "tony"
    [14]=>
    string(3) "tom"
}*/
```
* 数组最后一个元素后面可以加上分割符逗号，也可以不加，可视具体情况而定，如：
```php
$arr = ['12' => 'tony', '14' => 'tom'];
echo count($arr).'<br/>'; // 2
echo implode(',', $arr).'<br/>'; // tony,tom
$arr = ['12' => 'tony', '14' => 'tom',];
echo implode(',', $arr).'<br/>'; // tony,tom
echo count($arr).'<br/>'; // 2
```
* 数组元素的键只能是整数或者字符串，值可以是任意类型的数据。
```php
$four_king = ['刘德华', '张学友', '黎明', '郭富城'];
$arr = [
    true => 'true',
    false => 'false',
    2.6 => 2.6,
    NULL => NULL,
    // $four_king => 'four_king', // 网页无法正常运作
];
echo '<pre>';
var_dump($arr);
echo '</pre>';
/*
array(4) {
    [1]=>
    string(4) "true"
    [0]=>
    string(5) "false"
    [2]=>
    float(2.6)
    [""]=>
    NULL
}
*/
```
* 如果数组中多个元素的键名相等，则最后一个会覆盖前面的所有的同键元素。
```php
$arr = [
    1 => 2,
    2 => 3,
    3 => 4,
    1 => 5,
    1 => 6,
];
echo '<pre>';
print_r($arr);
echo '</pre>';
/*
Array
(
    [1] => 6
    [2] => 3
    [3] => 4
)
*/
```
* 在一个数组中如果没有指定某个元素的键，怎该元素会以当前最大索引值加1做为键，键从0开始。
```php
$four_king = ['刘德华', '张学友', 5 => '黎明', '郭富城'];
echo '<pre>';
print_r($four_king);
echo '</pre>';
/*
Array
(
    [0] => 刘德华
    [1] => 张学友
    [5] => 黎明
    [6] => 郭富城
)
*/
```
* 负数可以作为数组的键。
```php
$four_king = ['刘德华', '张学友', -85 => '黎明', '郭富城'];
echo '<pre>';
print_r($four_king);
echo '</pre>';
/*
Array
(
    [0] => 刘德华
    [1] => 张学友
    [-85] => 黎明
    [2] => 郭富城
)
*/
```
* 可以通过`数组变量[键]`或`数组变量{键}`的形式访问一个数组元素的值。
```php
$four_king = ['andy' => '刘德华', '张学友', -85 => '黎明', '郭富城'];
echo $four_king['andy'].'<br/>'; // 刘德华
echo $four_king{-85}.'<br/>'; // 黎明
var_dump($four_king[100]); // NULL
```
* 可以通过`数组变量[键]`或`数组变量{键}`的形式修改一个数组元素的值，通过`数组变量[]`或`数组变量[键]`的形式追加一个数组元素。
```php
$arr = ['andy' => '刘德华', '张学友', -85 => '黎明', '郭富城'];
$arr['andy'] = '谭咏麟';
echo '<pre>';
print_r($arr);
echo '<pre>';
$arr{1} = '窦唯';
echo '<pre>';
print_r($arr);
echo '<pre>';
$arr[] = '王杰';
echo '<pre>';
print_r($arr);
echo '<pre>';
// $arr{} = '王菲'; // 网页无法正常运作
echo '<pre>';
print_r($arr);
echo '<pre>';
$arr['king'] = 'michael jackson';
echo '<pre>';
print_r($arr);
echo '<pre>';
/*
Array
(
    [andy] => 谭咏麟
    [0] => 张学友
    [-85] => 黎明
    [1] => 郭富城
)
Array
(
    [andy] => 谭咏麟
    [0] => 张学友
    [-85] => 黎明
    [1] => 窦唯
)
Array
(
    [andy] => 谭咏麟
    [0] => 张学友
    [-85] => 黎明
    [1] => 窦唯
    [2] => 王杰
)
Array
(
    [andy] => 谭咏麟
    [0] => 张学友
    [-85] => 黎明
    [1] => 窦唯
    [2] => 王杰
)
Array
(
    [andy] => 谭咏麟
    [0] => 张学友
    [-85] => 黎明
    [1] => 窦唯
    [2] => 王杰
    [king] => michael jackson
)
*/
ini_set('display_errors', 'on');
error_reporting(E_ALL);
$person[] = '黄家驹';
echo '<pre>';
print_r($person);
echo '<pre>';
$person = '黄家驹';
$person = ['黄家驹'];
echo '<pre>';
print_r($person);
echo '<pre>';
$person = '黄家驹';
$person[] = '黄家驹';
echo '<pre>';
var_dump($person);
echo '<pre>';
/*
Array
(
    [0] => 黄家驹
)
Array
(
    [0] => 黄家驹
)


Fatal error:  [] operator not supported for strings in /Library/WebServer/Documents/index.php on line 14
*/
```
* 可以使用`unset()`函数来注销一个数组元素或者注销数组本身。
```php
$person = ['jack', 'andy', 'tom', 'jim', 'lily'];
echo '<pre>';
print_r($person);
echo '<pre>';
unset($person[4]);
echo '<pre>';
print_r($person);
echo '<pre>';
$person[] = 'lucy';
echo '<pre>';
print_r($person);
echo '<pre>';
unset($person);
echo '<pre>';
var_dump($person);
echo '<pre>';
$person[] = 'honey';
echo '<pre>';
print_r($person);
echo '<pre>';
$person = ['jack', 'andy', 'tom', 'jim', 'lily'];
echo '<pre>';
print_r($person);
echo '<pre>';
unset($person[2]);
unset($person[4]);
$person[] = 'lucy';
echo '<pre>';
print_r($person);
echo '<pre>';
$person = array_values($person);
echo '<pre>';
print_r($person);
echo '<pre>';
$person[] = 'honey';
echo '<pre>';
print_r($person);
echo '<pre>';
/*
Array
(
    [0] => jack
    [1] => andy
    [2] => tom
    [3] => jim
    [4] => lily
)
Array
(
    [0] => jack
    [1] => andy
    [2] => tom
    [3] => jim
)
Array
(
    [0] => jack
    [1] => andy
    [2] => tom
    [3] => jim
    [5] => lucy
)
NULL
Array
(
    [0] => honey
)
Array
(
    [0] => jack
    [1] => andy
    [2] => tom
    [3] => jim
    [4] => lily
)
Array
(
    [0] => jack
    [1] => andy
    [3] => jim
    [5] => lucy
)
Array
(
    [0] => jack
    [1] => andy
    [2] => jim
    [3] => lucy
)
Array
(
    [0] => jack
    [1] => andy
    [2] => jim
    [3] => lucy
    [4] => honey
)
*/
```
* 在访问字符串下标(键)的数组元素时，要在下标(键)上加引号。
```php
ini_set('display_errors', 'on');
error_reporting(E_ALL);
$arr = ['andy' => '刘德华', '张学友', -85 => '黎明', '郭富城'];
echo $arr['andy'].'<br/>'; // 刘德华
echo $arr["andy"].'<br/>'; // 刘德华
echo $arr[andy].'<br/>'; 
// Notice: Use of undefined constant andy - assumed 'andy' in /Library/WebServer/Documents/index.php on line 6
// 刘德华
const andy = 1;
echo $arr[andy].'<br/>'; // 郭富城
```
* 当一个数组的元素也是一个数组的时候，这个数组就成了多维数组
```php
$arr = ['andy' => '刘德华', '张学友', -85 => '黎明', '郭富城'];
echo '<pre>';
print_r($arr);
echo '<pre>';
$arr['child'] = ['jack', 'andy', 'tom', 'jim', 'lily'];
echo '<pre>';
print_r($arr);
echo '<pre>';
$arr['child'][] = [
    2 => 3,
    4 => 5,
    6 => 7,
];
echo '<pre>';
print_r($arr);
echo '<pre>';
/*
Array
(
    [andy] => 刘德华
    [0] => 张学友
    [-85] => 黎明
    [1] => 郭富城
)
Array
(
    [andy] => 刘德华
    [0] => 张学友
    [-85] => 黎明
    [1] => 郭富城
    [child] => Array
        (
            [0] => jack
            [1] => andy
            [2] => tom
            [3] => jim
            [4] => lily
        )

)
Array
(
    [andy] => 刘德华
    [0] => 张学友
    [-85] => 黎明
    [1] => 郭富城
    [child] => Array
        (
            [0] => jack
            [1] => andy
            [2] => tom
            [3] => jim
            [4] => lily
            [5] => Array
                (
                    [2] => 3
                    [4] => 5
                    [6] => 7
                )

        )

)
*/
```