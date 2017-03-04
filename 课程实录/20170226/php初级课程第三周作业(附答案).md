* 请定义一个变量$x并赋值为1，再定义一个变量$y并赋值为2，然后对$x和$y进行全部可用二元算数运算符进行运算，将得到的值赋值给变量$z，然后分别进行输出。
```php
$x = 1;
$y = 2;
$z = $x + $y;
echo $z.'<br/>';
$z = $x - $y;
echo $z.'<br/>';
$z = $x * $y;
echo $z.'<br/>';
$z = $x / $y;
echo $z.'<br/>';
$z = $x % $y;
echo $z.'<br/>';
$z = $x ** $y;
echo $z.'<br/>';
/*
3
-1
2
0.5
1
1
*/
```
* 请定义一个变量$x并赋值为1，再定义一个变量$y并赋值为2，然后对$x和$y进行全部可用二元算数运算符进行运算，将得到的值以复合形式赋值给变量$x，然后分别进行变量$x的输出。
```php
$x = 1;
$y = 2;
$x += $y;
echo $x.'<br/>';
$x -= $y;
echo $x.'<br/>';
$x *= $y;
echo $x.'<br/>';
$x /= $y;
echo $x.'<br/>';
$x %= $y;
echo $x.'<br/>';
$x **= $y;
echo $x.'<br/>';
/*
3
1
2
1
1
1
*/
```
* 对于给定的数字13和17，请进行按位与和按位或运算，请分别以程序和手算的形式获取结果。
```php
// 13 & 17 => 01101 & 10001 => 00001 => 1
// 13 & 17 => 01101 | 10001 => 11101 => 29

echo 13 & 17;
echo '<br/>';
echo 13 | 17;
/*
1
29
*/
```
* 对于给定的数字13和-17，请进行按位取反运算，请分别以程序和手算的形式获取结果。
```php
// 13 => 0000 0000 0000 1101 => 1111 1111 1111 0010 => 1111 1111 1111 0001 => 1000 0000 0000 1110 => -14
// -17 => 1000 0000 0001 0001 => 1000 0000 0001 0000 => 1111 1111 1110 1111 => 0000 0000 0001 0000 => 16

echo ~13;
echo '<br/>';
echo ~-17;
/*
-14
16
*/
```
* 对于给定的数字15，请进行按位右移和左移操作，请分别以程序和手算的形式获取结果。
```php
// 15 >> 1 => 1111 >> 1 => 0111 => 7
// 15 << 1 => 1111 << 1 => 1 1110 => 30

echo 15 >> 1;
echo '<br/>';
echo 15 << 1;
/*
7
30
*/ 
```
* 请用所有学到过的比较运算符对数字13和17进行比较并输出结果。
```php
var_dump(13 > 17);
echo '<br/>';
var_dump(13 >= 17);
echo '<br/>';
var_dump(13 < 17);
echo '<br/>';
var_dump(13 <= 17);
echo '<br/>';
var_dump(13 == 17);
echo '<br/>';
var_dump(13 === 17);
echo '<br/>';
var_dump(13 != 17);
echo '<br/>';
var_dump(13 !== 17);
echo '<br/>';
var_dump(13 <> 17);
echo '<br/>';
var_dump(13 > 17 ? 1 : 0);
echo '<br/>';
/*
bool(false) 
bool(false) 
bool(true) 
bool(true) 
bool(false) 
bool(false) 
bool(true) 
bool(true) 
bool(true) 
int(0) 
*/
```
* 请抑制一个未定义变量错误并通过程序获取被抑制的错误同时打印出这个错误。
```php
echo @$a;
echo '<br/>';
echo $php_errormsg;
```
* 请使用执行运算符打印出当前文件夹下所有文件和文件夹。
```php
$dir = `dir`;
echo $dir;
```
* 对于给定的值为5的变量$x，请对其分别进行两种形式的递增和递减，然后输出运算后的结果。
```php
$x = 5;
echo $x++;
echo '<br/>';
echo $x;
echo '<br/>';
echo $x--;
echo '<br/>';
echo $x;
echo '<br/>';
echo ++$x;
echo '<br/>';
echo $x;
echo '<br/>';
echo --$x;
echo '<br/>';
echo $x;
/*
5
6
6
5
6
6
5
5
*/
```
* 对于给定的值为TRUE的变量$x和值为FALSE的变量$y，请使用所有学过的逻辑运算符进行运算，将得到的结果带类型打印出来。
```php
$x = TRUE;
$y = FALSE;
var_dump($x and $y);
echo '<br/>';
var_dump($x or $y);
echo '<br/>';
var_dump($x && $y);
echo '<br/>';
var_dump($x || $y);
echo '<br/>';
var_dump($x xor $y);
echo '<br/>';
var_dump(!$x);
echo '<br/>';
var_dump(!$y);
echo '<br/>';
/*
bool(false) 
bool(true) 
bool(false) 
bool(true) 
bool(true) 
bool(false) 
bool(true) 
*/
```
* 对于给定的值为'hello, everybody!'字符串变量$x,请用复合赋值形式将字符串'I am superman'拼接到$x上并打印输出。
```php
$x = 'hello, everybody!';
$x .= 'I am superman';
echo $x;
// hello, everybody!I am superman
```
* 请定义两个数组变量，然后对其进行可能的所有数据运算操作，把结果打印出来。
```php
<?php
$a = [1, 2, 3];
$b = [4, 5, 6];
echo '<pre>';
print_r($a + $b);
echo '</pre>';
echo '<pre>';
var_dump($a == $b);
echo '</pre>';
echo '<pre>';
var_dump($a === $b);
echo '</pre>';
echo '<pre>';
var_dump($a != $b);
echo '</pre>';
echo '<pre>';
var_dump($a !== $b);
echo '</pre>';
echo '<pre>';
var_dump($a <> $b);
echo '</pre>';
/*
Array
(
    [0] => 1
    [1] => 2
    [2] => 3
)
bool(false)
bool(false)
bool(true)
bool(true)
bool(true)
*/
```
