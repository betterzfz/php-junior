#### 流程控制的概念
通过流程控制可以实现抽象的逻辑需求，可以有条件地控制代码的执行，可以自由地对代码进行循环执行来实现数据的读取和处理。

#### 条件控制结构
条件控制结构主要包括`if`和`switch`两种。
```php
$x = 5;
$y = 3;

if($x > $y)
    echo '$x is bigger than $y'; // $x is bigger than $y

echo '<br/>';
if ($x > $y)
    echo '$x is bigger than $y'; // $x is bigger than $y

echo '<br/>';

if($x > $y){
    echo '$x is bigger than $y'; // $x is bigger than $y
}

echo '<br/>';

if ($x > $y) {
    echo '$x is bigger than $y'; // $x is bigger than $y
}

echo '<br/>';

if ($x > $y):
    echo '$x is bigger than $y'; // $x is bigger than $y
endif;

echo '<br/>';

if ($x > $y) {
    echo '$y is smaller than $x'; // $y is smaller than $x
}

echo '<br/>';

if ($x > $y) {
    echo '$x is bigger than $y'; // $x is bigger than $y
    echo '<br/>';
    echo '$y is smaller than $x'; // $x is smaller than $y
}

$y = 6;
if ($x > $y)
    echo '$x is bigger than $y'; // 没有输出
    echo '<br>';
    echo '$y is smaller than $x'; // $y is smaller than $x
    echo '<br>';

if ($x < $y):
    echo '$x is smaller than $y'; // $x is smaller than $y
    echo '<br>';
    echo '$y is bigger than $x'; // $y is bigger than $x
endif;

echo '<br/>';

$z = 7;
if ($x < $y)
    if ($y < $z)
        echo '$z is the biggest'; // $z is the biggest

echo '<br/>';

if ($x < $y) {
    if ($y < $z) {
        echo '$z is the biggest'; // $z is the biggest
    }
}

echo '<br/>';
```
* `if`条件控制结构使得代码可以根据指定条件有选择地进行执行。
* `if`条件中的表达式取得的值为布尔值，程序会根据该值有选择地执行代码。
* `if`条件控制结构中如果某个执行段的语句数大于1则需要用`{`和`}`进行围绕。
* `if`条件控制结构可以进行嵌套。

```php
$x = 5;
$y = 7;
if ($x > $y) {
    echo '$x is bigger than $y';
} else {
    echo '$x is not bigger than $y';
}
// $x is not bigger than $y
echo '<br/>';
if ($x > $y)
    echo '$x is bigger than $y';
else
    echo '$x is not bigger than $y';
// $x is not bigger than $y
echo '<br/>';
if ($x > $y):
    echo '$x is bigger than $y';
else:
    echo '$x is not bigger than $y';
endif;
// $x is not bigger than $y
echo '<br/>';

if ($x < $y) {
    echo '$x is smaller than $y';
} else {
    echo '$x is not smaller than $y';
    echo '$x may be equal to $y';
}
// $x is smaller than $y
echo '<br/>';
if ($x < $y)
    echo '$x is smaller than $y';
else
    echo '$x is not smaller than $y';
    echo '<br/>';
    echo '$x may be equal to $y';
// $x is smaller than $y
// $x may be equal to $y
echo '<br/>';
if ($x < $y):
    echo '$x is smaller than $y';
else:
    echo '$x is not smaller than $y';
    echo '<br/>';
    echo '$x may be equal to $y';
endif;
// $x is smaller than $y
echo '<br/>';
```
* `if...else...`中的`else`结构定义了条件不成立时所要执行的代码片段。

```php
$x = 5;
$y = 7;
if ($x > $y) {
    echo '$x is bigger than $y';
} else if ($x == $y) {
    echo '$x is equal to $y';
} else {
    echo '$x is smaller than $y';
}
// $x is smaller than $y
echo '<br/>';

if ($x > $y)
    echo '$x is bigger than $y';
else if ($x == $y)
    echo '$x is equal to $y';
else
    echo '$x is smaller than $y';
// $x is smaller than $y
echo '<br/>';

/*if ($x > $y):
    echo '$x is bigger than $y';
else if ($x == $y): // 网页无法正常运作
    echo '$x is equal to $y';
else:
    echo '$x is smaller than $y';
echo '<br/>';*/
if ($x > $y):
    echo '$x is bigger than $y';
elseif ($x == $y): // 网页无法正常运作
    echo '$x is equal to $y';
else:
    echo '$x is smaller than $y';
endif;
// $x is smaller than $y
echo '<br/>';

if ($x < $y) {
    echo '$x is smaller than $y';
} else if ($x == $y) {
    echo '$x is equal to $y';
    echo '<br/>';
    echo '$x = $y';
} else {
    echo '$x is bigger than $y';
    echo '<br/>';
    echo '$x = $y';
}
// $x is smaller than $y
echo '<br/>';

if ($x < $y)
    echo '$x is smaller than $y';
else if ($x == $y)
    echo '$x is equal to $y';
    // echo '$x = $y'; // 网页无法正常运作
else
    echo '$x is bigger than $y';
    echo '<br/>';
    echo '$x = $y';
// $x is smaller than $y
// $x = $y
echo '<br/>';

if ($x < $y):
    echo '$x is smaller than $y';
elseif ($x == $y):
    echo '$x is equal to $y';
    // echo '$x = $y'; // 网页无法正常运作
else:
    echo '$x is bigger than $y';
    echo '<br/>';
    echo '$x = $y';
endif;
// $x is smaller than $y
echo '<br/>';

if (1 == $x) {
    echo '$x is equal to 1';
    echo '<br/>';
} else if (2 == $x) {
    echo '$x is equal to 2';
    echo '<br/>';
} else if (3 == $x) {
    echo '$x is equal to 3';
    echo '<br/>';
} else if (4 == $x) {
    echo '$x is equal to 3';
    echo '<br/>';
}  else if (5 == $x) {
    echo '$x is equal to 5';
    echo '<br/>';
} else {
    echo '$x is bigger than 5';
    echo '<br/>';
}
// $x is equal to 5
if (1 == $x):
    echo '$x is equal to 1';
    echo '<br/>';
elseif (2 == $x):
    echo '$x is equal to 2';
    echo '<br/>';
elseif (3 == $x):
    echo '$x is equal to 3';
    echo '<br/>';
elseif (4 == $x):
    echo '$x is equal to 3';
    echo '<br/>';
elseif (5 == $x):
    echo '$x is equal to 5';
    echo '<br/>';
else:
    echo '$x is bigger than 5';
    echo '<br/>';
endif;
// $x is equal to 5
```
* `else if`和`elseif`可以用于多重条件控制，当该结构前面的`if`或`else if`（`elseif`)都为假且当前的结构中的表达式为真时则执行这一控制结构中的代码。
* `else if`和`elseif`的功能在用花括号包围结构代码时没有区别的，但当冒号定义的添加中只能用`elseif`，否则会产生解析错误。

```php
$x = 5;
switch($x){
	case 0:
		echo '$x is equal to 0';
		break;
	case 1:
		echo '$x is equal to 1';
		break;
	case 2:
		echo '$x is equal to 2';
		break;
	case 3:
		echo '$x is equal to 3';
		break;
	case 4:
		echo '$x is equal to 4';
		break;
	case 5:
		echo '$x is equal to 5';
		break;
}
// $x is equal to 5
echo '<br/>';
$x++;
switch($x){
	case 0:
		echo '$x is equal to 0';
		break;
	case 1:
		echo '$x is equal to 1';
		break;
	case 2:
		echo '$x is equal to 2';
		break;
	case 3:
		echo '$x is equal to 3';
		break;
	case 4:
		echo '$x is equal to 4';
		break;
	case 5:
		echo '$x is equal to 5';
		break;
	default:
		echo '$x is bigger than 5';
		break;
}
// $x is bigger than 5
echo '<br/>';
switch ($x) {
	case 0:
		echo '$x is equal to 0';
		break;
	case 1:
		echo '$x is equal to 1';
		break;
	case 2:
		echo '$x is equal to 2';
		break;
	case 3:
		echo '$x is equal to 3';
		break;
	case 4:
		echo '$x is equal to 4';
		break;
	case 5:
		echo '$x is equal to 5';
		break;
	default:
		echo '$x is bigger than 5';
		break;
}
// $x is bigger than 5
echo '<br/>';
switch ($x) {
	case 0:
		echo '$x is equal to 0';
		echo '<br/>';
		break;
	case 1:
		echo '$x is equal to 1';
		echo '<br/>';
		break;
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
		break;
	case 3:
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4:
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5:
		echo '$x is equal to 5';
		echo '<br/>';
		break;
	default:
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
}
// $x is bigger than 5
switch($x):
	case 0:
		echo '$x is equal to 0';
		echo '<br/>';
		break;
	case 1:
		echo '$x is equal to 1';
		echo '<br/>';
		break;
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
		break;
	case 3:
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4:
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5:
		echo '$x is equal to 5';
		echo '<br/>';
		break;
	default:
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
endswitch;
// $x is bigger than 5
switch ($x):
	case 0:
		echo '$x is equal to 0';
		echo '<br/>';
		break;
	case 1:
		echo '$x is equal to 1';
		echo '<br/>';
		break;
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
		break;
	case 3:
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4:
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5:
		echo '$x is equal to 5';
		echo '<br/>';
		break;
	default:
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
endswitch;
// $x is bigger than 5
switch ($x) {
	case 0;
		echo '$x is equal to 0';
		echo '<br/>';
		break;
	case 1;
		echo '$x is equal to 1';
		echo '<br/>';
		break;
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
		break;
	case 3;
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4;
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5;
		echo '$x is equal to 5';
		echo '<br/>';
		break;
	default;
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
}
// $x is bigger than 5
$x = 1;
switch ($x) {
	case 0;
		echo '$x is equal to 0';
		echo '<br/>';
	case 1;
		echo '$x is equal to 1';
		echo '<br/>';
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
	case 3;
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4;
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5;
		echo '$x is equal to 5';
		echo '<br/>';
		break;
	default;
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
}
// $x is equal to 1
// $x is equal to 2
// $x is equal to 3
switch ($x) {
	default;
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
	case 0;
		echo '$x is equal to 0';
		echo '<br/>';
	case 1;
		echo '$x is equal to 1';
		echo '<br/>';
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
	case 3;
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4;
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5;
		echo '$x is equal to 5';
		echo '<br/>';
		break;
}
/*
$x is equal to 1
$x is equal to 2
$x is equal to 3
*/
$x = 8;
switch ($x) {
	default;
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
	case 0;
		echo '$x is equal to 0';
		echo '<br/>';
	case 1;
		echo '$x is equal to 1';
		echo '<br/>';
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
	case 3;
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4;
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5;
		echo '$x is equal to 5';
		echo '<br/>';
		break;
}
// $x is bigger than 5
$x = 3;
switch ($x) {
	default;
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
	case 0;
		echo '$x is equal to 0';
		echo '<br/>';
	case 1;
		echo '$x is equal to 1';
		echo '<br/>';
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
	case 3;
		echo '$x is equal to 3';
		echo '<br/>';
		break;
	case 4;
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 5;
		echo '$x is equal to 5';
		echo '<br/>';
		break;
}
// $x is equal to 3
switch ($x) {
	default;
		echo '$x is bigger than 5';
		echo '<br/>';
		break;
	case 5;
		echo '$x is equal to 5';
		echo '<br/>';
		break;
	case 0;
		echo '$x is equal to 0';
		echo '<br/>';
	case 1;
		echo '$x is equal to 1';
		echo '<br/>';
	case 4;
		echo '$x is equal to 4';
		echo '<br/>';
		break;
	case 2:
		echo '$x is equal to 2';
		echo '<br/>';
	case 3;
		echo '$x is equal to 3';
		echo '<br/>';
		break;
}
// $x is equal to 3
$name = 'stone';
switch($name){
	case 'andy':
		echo 'my name is andy';
		break;
	case 'jack':
		echo 'my name is jack';
		break;
	case 'stone':
		echo 'my name is stone';
		break;
	case 'lucy':
		echo 'my name is lucy';
		break;
	default:
		echo 'I have no name';
		break;
}
// my name is stone
echo '<br/>';
$name = 'Stone';
switch($name){
	case 'andy':
		echo 'my name is andy';
		break;
	case 'jack':
		echo 'my name is jack';
		break;
	case 'STONE':
	case 'Stone':
	case 'stone':
		echo 'my name is stone';
		break;
	case 'lucy':
		echo 'my name is lucy';
		break;
	default:
		echo 'I have no name';
		break;
}
// my name is stone
echo '<br/>';
```
#### 循环控制结构
在`php`中，常用的循环控制结构包括`while`, `do-while`, `for`以及`foreach`。
```php
$i = 0;
while ($i <= 9) {
    echo $i;
    $i++;
}
// 0123456789
echo '<br/>';
// 当while表达式的值为TRUE时执行循环体中的内容，while表达式的值在开始循环时检查，所以while循环有可能一次都不执行
$i = 0;
while($i <= 9){
    echo $i;
    $i++;
}
// 0123456789
echo '<br/>';
$i = 0;
while ($i <= 9):
    echo $i;
    $i++;
endwhile;
// 0123456789
echo '<br/>';
$i = 0;
while($i <= 9):
    echo $i;
    $i++;
endwhile;
// 0123456789
echo '<br/>';
$i = 0;
while ($i <= 9)
    $i++;
echo $i;
// 10
echo '<br/>';
$i = 0;
do {
	echo $i;
	$i++;
} while ($i < 10);
// 0123456789
echo '<br/>';
// do-while循环每次在结束时检查循环表达式，所以此种循环至少会执行一次

$i = 0;
do
	$i++;
while ($i < 10);
echo $i; // 10
echo '<br/>';

$i = 0;
do{
	echo $i;
	$i++;
}while($i < 10);
// 0123456789
echo '<br/>';

$i = 0;
do {
	if ($i > 9) {
		break;
	}
	echo $i++;
} while (TRUE);
// 0123456789
// 可以不控制循环表达式，在循环体内通过break跳出循环
echo '<br/>';


for ($i = 0;$i < 10;$i++) {
	echo $i;
}
// 0123456789
// for循环的结构为：for (expr1; expr2; expr3) statement, 其中每个表达式都可以为空或是用逗号分隔的多个表达式。expr1和expr2在循环开始前一定会执行一次。expr2如果为真则执行循环体，否则终止循环，当有多个表达式用逗号分隔时以最后一个表达的值为准。expr3在每次循环后执行。
echo '<br/>';

for ($i = 0;$i < 10;$i++)
	echo $i;
// 0123456789
// 当循环体只有一条语句时可以省略花括号，但是这个做是不推荐的，始终带有花括号的循环结构看起来更清晰
echo '<br/>';

for ($i = 0;;$i++) {
	if ($i > 9) {
		break;
	}
	echo $i;
}
// 0123456789
echo '<br/>';

$i = 0;
for (;;) {
	if ($i > 9) {
		break;
	}
	echo $i++;
}
// 0123456789
echo '<br/>';

// for ($i = 0, $j = 0;$j = $i, $i < 10;$j++, echo $j, echo '<br/>', echo $i, $i++); // Parse error: syntax error, unexpected 'echo' (T_ECHO)
for ($i = 0, $j = 0;$j = $i, $i < 10;$j++, print $j, print '<br/>', print $i, $i++); 
/*
1
02
13
24
35
46
57
68
79
810
9
 */
echo '<br/>';

for ($i = 0;$i < 10;$i++):
	echo $i;
endfor;
// 0123456789
echo '<br/>';


// foreach提供一种用于遍历数据或对象的方式
$four_kings = ['刘德华', '张学友', '黎明', '郭富城'];
foreach ($four_kings as $value) {
	echo $value;
	echo '<br/>';
}
/*
刘德华
张学友
黎明
郭富城
 */

foreach ($four_kings as $value)
	echo $value;
	echo '<br/>';
// 刘德华张学友黎明郭富城

foreach ($four_kings as $key => $value) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
}
/*
key:0 => value:刘德华
key:1 => value:张学友
key:2 => value:黎明
key:3 => value:郭富城
 */

// foreach开始执行时，数组内部的指针会自动指向第一个单元，不需要像其它循环遍历那样在循环前调用reset()
// reset()是一个函数，用于将数组内部指针指向第一个单元
while (list($key, $value) = each($four_kings)) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
	if ($key > 1) {
		break;
	}
}
/*
key:0 => value:刘德华
key:1 => value:张学友
key:2 => value:黎明
 */
while (list($key, $value) = each($four_kings)) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
}
// key:3 => value:郭富城
// each()函数用于返回数组中当前的键值对并将数组指针向前移一步
// list()函数用于把数组中的值赋值给一些变量
foreach ($four_kings as $key => $value) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
	if ($key > 1) {
		break;
	}
}
/*
key:0 => value:刘德华
key:1 => value:张学友
key:2 => value:黎明
 */
echo '<hr/>';
foreach ($four_kings as $key => $value) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
}
/*
key:0 => value:刘德华
key:1 => value:张学友
key:2 => value:黎明
key:3 => value:郭富城
 */
while (list($key, $value) = each($four_kings)) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
	if ($key > 1) {
		break;
	}
}
// 此处输出为空，如果不在意$key则while中的表达式可以写成list(, $value) = each($four_kings)
reset($four_kings);
while (list($key, $value) = each($four_kings)) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
	if ($key > 1) {
		break;
	}
}
/*
key:0 => value:刘德华
key:1 => value:张学友
key:2 => value:黎明
 */
reset($four_kings);
while (list($key, $value) = each($four_kings)) {
	echo 'key:'.$key.' => value:'.$value;
	echo '<br/>';
}
/*
key:0 => value:刘德华
key:1 => value:张学友
key:2 => value:黎明
key:3 => value:郭富城
 */
echo '<hr/>';
$arr = [
	'zero' => [0, 1, 2 ,3],
	'two' => [4, 5, 6 ,7],
	'three' => [8, 9],
];
foreach ($arr as $key => $value) {
	echo 'key:'.$key.'<br/>';
	foreach ($value as $k => $v) {
		echo 'k='.$k.' => v='.$v;
		echo '<br/>';
	}
}
/*
key:zero
k=0 => v=0
k=1 => v=1
k=2 => v=2
k=3 => v=3
key:two
k=0 => v=4
k=1 => v=5
k=2 => v=6
k=3 => v=7
key:three
k=0 => v=8
k=1 => v=9
 */
$arr = [
	'zero' => [0, 1, 2],
	'two' => [3, 4, 5],
	'three' => [6, 7, 8],
];
foreach ($arr as list($i, $j, $k)) {
	echo '$i:'.$i.', $j:'.$j.', $k:'.$k;
	echo '<br/>';
}
/*
$i:0, $j:1, $k:2
$i:3, $j:4, $k:5
$i:6, $j:7, $k:8
 */
foreach ($arr as list(, $j, $k, $m)) {
	echo '$j:'.$j.', $k:'.$k.', $m:'.$m;
	echo '<br/>';
}
/*
Notice: Undefined offset: 3 
$j:1, $k:2, $m:

Notice: Undefined offset: 3 
$j:4, $k:5, $m:

Notice: Undefined offset: 3 
$j:7, $k:8, $m:
 */
```
# 流程跳转结构

