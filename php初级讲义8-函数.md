#### 函数的概念
函数是对一组操作的封装。
#### 自定义函数
自定义函数是用户根据需求自己封装的一组操作。
```php
function get_my_name($name){
    return 'my name is '.$name;
}
echo get_my_name('lilei'); // my name is lilei
echo '<br/>';

ini_set('display_errors', 'on');
error_reporting(E_ALL);

/*function 1_get_number($i){ // 网页无法正常运作
    return 'I get a number:'.$i;
}*/
/*function get_number%_($i){ // 网页无法正常运作
    return 'I get a number:'.$i;
}*/

echo add_function(1, 2); // 3
echo '<br/>';
function add_function($x, $y){
    return $x + $y;
}

$bool = FALSE;
// var_dump(get_a_bool($bool)); // Fatal error: Call to undefined function get_a_bool()
echo '<br>';
if ($bool) {
    function get_a_bool($bool){
        return $bool;
    }
}
// get_a_bool($bool); // Fatal error: Call to undefined function get_a_bool()
echo '<br>';
if ($bool) {
    var_dump(get_a_bool($bool)); // bool(true) 
    echo '<br>';
}

function have_a_function(){
    function another_function(){
        return 'I am anther function';
    }
    return 'I have a function';
}

// echo another_function(); // Fatal error: Call to undefined function another_function()
echo '<br>';
echo have_a_function(); // I have a function
echo '<br>';
echo another_function(); // I am anther function
echo '<br>';

function use_a_function($x, $y){
    return add_function($x, $y);
}

echo use_a_function(1, 2);
echo '<br>'; // 3
/*function another_function(){ // Fatal error: Cannot redeclare another_function()
    return 'I am anther function';
}*/
echo Another_function(); // I am anther function
echo '<br>';
echo Another_Function(); // I am anther function
echo '<br>';
echo Another_FUNCTION(); // I am anther function
echo '<br>';

function echo_x_10($x){
    if ($x <= 10) {
        echo $x;
        echo '<br/>';
        echo_x_10(++$x);
    }
}
echo_x_10(1);
/*
1
2
3
4
5
6
7
8
9
10
*/
```
- 合法的函数名应该由以字母，数字，下划线构成且不能以数字开头。
- 函数定义之前被调用，但如果函数的定义是有条件的则必须先定义再调用。
- 在`php`函数具有全局作用域，即可以在函数中定义和调用函数。
- 在`php`函数不能重复定义。
- 函数名对大小写不敏感，但是应该保持调用和定义的统一。
- 函数内部可以继续调用自身，这种行为被称为递归。
#### 函数参数
通过参数可以向函数传递信息，函数的参数可以是用逗号分隔的表达式列表。
```php
```
- 函数可以没有参数。
- 函数参数可以是任意合法的数据类型。
- 默认情况下，函数参数通过值传递，在函数内部改变参数的值并不会改变函数外部的值。
- 通过引用传递参数来允许函数修改它的参数值。
- 如果想要函数的一个参数总是通过引用传递，可以在函数定义中该参数的前面加上符号`&`。