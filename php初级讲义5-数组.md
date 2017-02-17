#### 定义
数组是一系列键值对的组合，键和值组成了数组的一个元素，元素之间用逗号隔开，键表示了元素的索引，值表示了元素的具体数据。数组的键可能是数字或字符串，值可以是任意合法的数据。

#### 语法
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

#### 说明
* 数组可分为一维数组和多维数组，当数组元素的值为一个数组时，该数组即为多维数组。
* 数组可分为用数字做键的索引数组，用字符串做键的关联数组以及混合了数字和字符串键的混合数组，这仅仅是人为的划分方便使用。
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