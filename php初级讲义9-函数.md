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
function have_no_paramater(){
    return 'This is a function without paramater';
}
echo have_no_paramater(); // This is a function without paramater
echo '<br/>';

function have_a_paramater($paramater){
    return 'This is a function has a paramater:'.$paramater;
}
echo have_a_paramater('paramater'); // This is a function has a paramater:paramater
echo '<br/>';

function person_introduction($name, $age){
    return 'my name is '.$name.', I am '.$age.' years old.';
}
echo person_introduction('lilei', '12'); // my name is lilei, I am 12 years old.
echo '<br/>';
function person_introduction_from_array($introduction){
    return 'my name is '.$introduction['name'].', I am '.$introduction['age'].' years old.';
}
echo person_introduction_from_array(['name' => 'lilei', 'age' => '12']); // my name is lilei, I am 12 years old.
echo '<br/>';

$y = 3;
function add_1($x){
	$x++;
	return $x;
}
echo add_1($y); // 4
echo '<br/>';
echo $y;
echo '<br/>'; // 3
function add_2(&$x){
	$x += 2;
	return $x;
}
echo add_2($y); // 5
echo '<br/>';
echo $y;
echo '<br/>'; // 5

function without_default_paramater($x){
	echo '$x='.$x;
	echo '<br/>';
}
without_default_paramater(); 
// Warning: Missing argument 1 for without_default_paramater(), called in ... and defined in ...
// Notice: Undefined variable: x in ...
// $x=

function with_default_paramater($x=5){
	echo '$x='.$x;
	echo '<br/>';
}
with_default_paramater(); // $x=5
with_default_paramater(7); // $x=7
$y = 4;
with_default_paramater($y); // $x=4

/*function with_default_paramater($x=$y){ // Parse error: syntax error, unexpected '$y' (T_VARIABLE) in
	echo '$x='.$x;
	echo '<br/>';
}*/


function without_default_paramater_return_value($x){
	return $x;
}
echo without_default_paramater_return_value(5); // 5
echo '<br/>';
/*function with_default_paramater($x=without_default_paramater_return_value(5)){ // Parse error: syntax error, unexpected '(', expecting ')' in
	echo '$x='.$x;
	echo '<br/>';
}*/
const NUMBER_PARAMATER = 8;
function with_default_paramater_const($x=NUMBER_PARAMATER){
	echo '$x='.$x;
	echo '<br/>';
}
with_default_paramater_const(); // $x=8

function with_two_paramater($x, $y = 4){
	echo '$x='.$x;
	echo '<br/>';
	echo '$y='.$y;
	echo '<br/>';
}
with_two_paramater(1);
with_two_paramater(3, 5);
/*
$x=1
$y=4
$x=3
$y=5
*/
function with_two_paramater_false($x = 5, $y){
	echo '$x='.$x;
	echo '<br/>';
	echo '$y='.$y;
	echo '<br/>';
}
with_two_paramater_false(1);
with_two_paramater_false(3, 5);
/*
Warning: Missing argument 2 for with_two_paramater_false(), called in 
$x=1

Notice: Undefined variable: y in 
$y=
$x=3
$y=5
*/
function with_reference_paramater(&$x = 5){
	$x++;
	echo '$x='.$x;
	echo '<br/>';
}
echo '$x='.$x;
echo '<br/>';
with_reference_paramater($x);
echo '<br/>';
echo '$x='.$x;
echo '<br/>';
/*
Notice: Undefined variable: x in D:\stone\wamp\Apache24\htdocs\test.php on line 79
$x=
$x=1

$x=1
*/

function with_another_reference_paramater($z = 5){
	$z++;
	echo '$z='.$z;
	echo '<br/>';
}
echo '$z='.$z;
echo '<br/>';
with_another_reference_paramater(&$z); 
// Fatal error: Call-time pass-by-reference has been removed; If you would like to pass argument by reference, modify the declaration of with_another_reference_paramater()
echo '<br/>';
echo '$z='.$z;
echo '<br/>';

function with_variable_paramater(...$args){
	echo '<pre>';
	print_r($args);
	echo '</pre>';
	foreach ($args as $key => $value) {
		echo '$key:'.$key.' => $value:'.$value;
		echo '<br/>';
	}
}
with_variable_paramater(1, 2, 3);
/*
Array
(
	[0] => 1
	[1] => 2
	[2] => 3
)

$key:0 => $value:1
$key:1 => $value:2
$key:2 => $value:3
*/
function with_two_paramater($x, $y){
	echo '$x='.$x.', $y='.$y;
	echo '<br/>';
}
with_two_paramater(...[1, 2]); // $x=1, $y=2

function with_type_paramater(array $a){
	echo '<pre>';
	print_r($a);
	echo '</pre>';
	foreach ($a as $key => $value) {
		echo '$key:'.$key.' => $value:'.$value;
		echo '<br/>';
	}
}

with_type_paramater([1, 2, 3]);
/*
Array
(
	[0] => 1
	[1] => 2
	[2] => 3
)

$key:0 => $value:1
$key:1 => $value:2
$key:2 => $value:3
*/
// with_type_paramater(1);
// Catchable fatal error: Argument 1 passed to with_type_paramater() must be of the type array, integer given, called in
// with_type_paramater(1, 2, 3);
// Catchable fatal error: Argument 1 passed to with_type_paramater() must be of the type array, integer given, called in

function with_int_paramater(int $x){
	return $x;
}

echo with_int_paramater(1); // 1
echo '<br/>';
echo with_int_paramater(1.5); // 1
declare(strict_types=1); // Fatal error: strict_types declaration must be the very first statement in the script in
echo with_int_paramater(1.5);

function callable_type_function(callable $func){
	$func();
}

function echo_hello(){
	echo 'hello';
}
callable_type_function('echo_hello'); // hello
callable_type_function('hello'); 
// Fatal error: Uncaught TypeError: Argument 1 passed to callable_type_function() must be callable, string given, called in

function with_bool_paramater(bool $a){
	var_dump($a);
}
with_bool_paramater(FALSE); // bool(false) 
echo '<br/>';
with_bool_paramater(2); // bool(true) 

function with_float_paramater(float $a){
	var_dump($a);
}
with_float_paramater(1.5); // float(1.5) 
echo '<br/>';
with_float_paramater(2); // float(2)  

function with_float_paramater(string $a){
	var_dump($a);
}
with_float_paramater('hello'); // string(5) "hello" 
echo '<br/>';
with_float_paramater(2); // string(1) "2"  
```
- 函数可以没有参数。
- 函数参数可以是任意合法的数据类型。
- 默认情况下，函数参数通过值传递，在函数内部改变参数的值并不会改变函数外部的值。
- 通过引用传递参数来允许函数修改它的参数值。
- 如果想要函数的一个参数总是通过引用传递，可以在函数定义中该参数的前面加上符号`&`。
- 通过使用默认参数可以在函数调用时不传递参数，默认参数应该放在所有非默认参数后面，默认参数不能为变量和函数调用，默认参数也可以通过引用传递。
- 可以通过`...`来为函数指定可变参数。
- 可以指定函数参数的类型，`php5.1.0`开始支持`array`， `php5.4.0`开始支持`callable`， `php7.0.0`开始支持`bool`, `float`, `int`, `string`等。 在非严格模式下，可能的类型转换会避免使用非指定类型参数的报错，严格模式下则不会进行类型转换而直接报错，可以通过`declare(strict_types=1)`来开启严格模式。

#### 函数的返回值
调用函数的目的通常是要获取一个结果，函数的返回值就提供了这样的结果，函数的返回值通过在函数体内的`return`指定，当函数指定了`return`则函数的执行就结束了。
```php
function add_function($x, $y){
	return $x + $y;
}
echo add_function(1, 2); // 3

function add_function($x, $y): float {
	return $x + $y;
}
var_dump(add_function(1, 2)); // float(3) 
```
- 可以指定函数的返回值类型。
- 如果没有指定`return`则返回值为`null`

#### 可变函数
通过变量来调用函数的可以被称为可变函数。
```php
function a_function(){
	return 'a function';
}
$function_name = 'a_function';
$string = $function_name();
echo $string; // a function
echo '<br/>';
echo $function_name();
```

#### 内置函数
`php`给我们提供了大量的内置函数，可以供我们直接使用。有的函数是由`php`核心提供的，无需配置直接使用，比如`var_dump()`。有的函数是要开启相应的扩展或在编译时指定才能使用的，比如`mysql_connect()`。

#### 匿名函数
`php`允许使用临时创建的没有名称的函数，这样的函数被称为匿名函数，也叫闭包函数。匿名函数通常被用作可执行的参数，如回调函数，当然还有其它的使用场景。
```php
function a_function($x, $y){
	return $y($x);
}
echo a_function(1, function($z){
	return ++$z;
}); // 2

$a_function = function(){
	return 'this is a function';
};
echo $a_function(); // this is a function

$hello = 'hello';
$get_variable = function(){
	return $hello;
};
echo $get_variable(); // Notice: Undefined variable: hello in

$get_variable = function() use ($hello){
	$hello = 'world';
	return $hello;
};
echo $get_variable(); // world
echo '<br/>';
echo $hello; // hello
echo '<br/>';
$get_variable_by_reference = function() use (&$hello){
	$hello = 'world';
	return $hello;
};
echo $get_variable_by_reference(); // world
echo '<br/>';
echo $hello; // world
echo '<br/>';
$z = 8;
$get_variables_by_reference = function(&$x, $y) use (&$hello){
	$x += $y;
	$hello = 'hello';
	return $hello;
};
echo $get_variables_by_reference($z, 6); // hello
echo '<br/>';
echo $hello; // hello
echo '<br/>';
echo $z; // 14
```
- 匿名函数可以赋值给一个变量，然后通过这个变量来调用这个函数。
- 匿名函数可以通过`use`从父作用域继承变量或按引用继承变量，在这种情况下也可以正常的使用参数。