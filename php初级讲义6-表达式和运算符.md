#### 表达式的定义
在`php`中任何有值的东西都是表达式。

#### 表达式的实例
```php
/**
 * 'hello, world!'是一个表达式，其值为'hello, world!'
 * $hello是一个表达式，其值在赋值之前是NULL，在赋值之后是'hello, world!'
 */
$hello = 'hello, world!';
echo $hello.'<br/>'; // hello, world!

/**
 * $title = $hello是一个表达式，其值为'hello, world!'
 * $title是一个表达式，其值在赋值之前是NULL，在赋值之后是'hello, world!'
 */
echo $title = $hello; // hello, world!
echo '<br/>';
echo $title.'<br/>'; // hello, world!
```

#### 表达式的说明
* 表达式可以组成语句但不是语句。

#### 运算符的定义
可以通过一个或多个值（表达式）产生另一个值（表达式）的符合被称为运算符。

#### 算数运算符
```php
$x = 5;
echo -$x; // -5 '-'为取反运算符 取到指定值的负值
echo '<br/>';
$y = -1;
echo -$y; // 1
echo '<br/>';
$z = $x + $y; // '+'为加法运算符 取得两个值的和
echo $z; // 4
echo '<br/>';
$z = $x - $y; // '-'为减法运算符 取得两个值的差
echo $z; // 6
echo '<br/>';
$z = $x * $y; // '*'为乘法运算符 取得两个值的乘积
echo $z; // -5
echo '<br/>';
$y = -2;
$z = $x / $y; // '/'为除法运算符 取得两个值的商
echo $z; // -2.5
echo '<br/>';
$z = $x % $y; // '%'为取模运算符 取得 $x 除以 $y 的余数
echo $z; // 1
echo '<br/>';
$z = $x ** $y; // '**'为求幂运算符 取得 $x 的 $y 次方 php >= 5.6
echo $z; // 0.04
echo '<br/>';
```
* 当操作数均为整数且能整除时，除法运算符得到结果为整数，除此之外都得到浮点数。
* 取模运算符的操作数在运算前会被舍去小数成整数，结果的符号与被除数相同。
```php
echo -5 % 2; // -1
echo '<br/>';
echo -5 % -2; // -1
echo '<br/>';
echo 5 % -2; // 1
echo '<br/>';
echo 5 % 2; // 1
echo '<br/>';
```

#### 赋值运算符
```php
$hello = 'hello, world!'; // '='是赋值运算符 把左边表达式的值赋值给右边
echo $hello; // hello, world!
echo '<br/>';
echo $title = $hello; // hello, world!
echo '<br/>';
echo $title; // hello, world!
echo '<br/>';

$title .= ' this is a title!'; // '.='是一个组合运算符 实现了字符串连接和赋值的组合
echo $title;
echo '<br/>'; // hello, world! this is a title!
$x = 5;
echo $x; // 5
echo '<br/>';
$x += 7; // '+='是一个组合运算符 实现了加法运算符和赋值运算符的组合
echo $x; // 12
echo '<br/>';
$x -= 3; // '-='是一个组合运算符 实现了减法运算符和赋值运算符的组合
echo $x; // 9
echo '<br/>';
$x *= 3; // '*='是一个组合运算符 实现了乘法运算符和赋值运算符的组合
echo $x; // 27
echo '<br/>';
$x /= 3; // '/='是一个组合运算符 实现了除法运算符和赋值运算符的组合
echo $x; // 9
echo '<br/>';
$x %= 5; // '%='是一个组合运算符 实现了取模运算符和赋值运算符的组合
echo $x; // 4
echo '<br/>';
$x **= 2; // '**='是一个组合运算符 实现了取幂运算符和赋值运算符的组合
echo $x; // 16
echo '<br/>';
```
* 赋值运算表达式也是有值，其值为右侧表达式的值。

#### 位运算符
通过位运算符可以对整数中指定的位进行求值等操作。
```php
// 对整数进行位运算都是以二进制的形式进行的
$x = 3;
$y = 5;
echo $x & $y; // 1 '&'是 按位与 运算符 当 $x 和 $y 中对应位都为1则结果该位为1 (0011 & 0101 => 0001 => 1)
echo '<br/>';
echo $x | $y; // 7 '|'是 按位或 运算符 当 $x 和 $y 中对应位有一个为1则结果该位为1 (0011 & 0101 => 0111 => 7)
echo '<br/>';
echo $x ^ $y; // 6 '^'是 按位异或 运算符 当 $x 和 $y 中对应位不同则结果该位为1 (0011 & 0101 => 0110 => 6)
echo '<br/>';
echo ~ $y; // -6 '~'是 按位取反 运算符 当 $y 中对应位1或0则结果该位为0或1
echo '<br/>';
/*
关于 ~ 5 = -6的解释
5的源码 0000 0000 0000 0000 0000 0000 0000 0101 
5的取反 1111 1111 1111 1111 1111 1111 1111 1010 补码
        1111 1111 1111 1111 1111 1111 1111 1001 反码
        1000 0000 0000 0000 0000 0000 0000 0110(-6) 源码
*/
echo $x >> 1; // 1 '>>'是 右移 运算符 按位向右移动 左侧以符号位填充 每次移动都表示除以2 (0011 >> 1 => 0001 => 1)
echo '<br/>';
echo $x << 1; // 6 '<<'是 左移 运算符 按位向左移动 右侧以0填充 每次移动都表示乘以2 (0011 << 1 => 0110 => 6)
echo '<br/>';
```
* 在位移运算中任何方向移出去的位都会被丢弃，左移符号不被保留，右移符号保留。

#### 比较运算符
可以通过比较运算符对两个值进行比较。
```php
$x = 1;
$y = 2;
var_dump($x == $y); // bool(false) '=='是用于判断两个值是否相等的比较运算符 结果为布尔值
echo '<br/>';
var_dump($x === '1'); // bool(false) '==='是用于判断两个值是否全等的比较运算符 值和类型都相等才能被认为是全等 结果为布尔值
echo '<br/>';
var_dump($x != $y); // bool(true) '!='是用于判断两个值是否不等的比较运算符 结果为布尔值
echo '<br/>';
var_dump($x !== '1'); // bool(true) '!=='是用于判断两个值是否不全等的比较运算符 值或类型不相等就认为是不全等 结果为布尔值
echo '<br/>';
var_dump($x <> $y); // bool(true) '<>'是用于判断两个值是否不等的比较运算符 结果为布尔值
echo '<br/>';
var_dump($x < $y); // bool(true) '<'是用于判断 $x 是否小于 $y 的比较运算符 结果为布尔值
echo '<br/>';
var_dump($x > $y); // bool(false) '>'是用于判断 $x 是否大于 $y 的比较运算符 结果为布尔值
echo '<br/>';
var_dump($x <= $y); // bool(true) '<='是用于判断 $x 是否小于等于 $y 的比较运算符 结果为布尔值
echo '<br/>';
var_dump($x >= $y); // bool(false) '>='是用于判断 $x 是否大于等于 $y 的比较运算符 结果为布尔值
echo '<br/>';
var_dump($x >= 1 ? 1 : -1); // int(1) '(1)?(2):(3)'是三元运算符 也是条件（比较）运算符 (1)为TRUE时(2)作为最终结果，否则(3)作为最终结果
echo '<br/>';
var_dump($x >= 1 ?: -1); // bool(true) '(1)?:(3)'是省略了中间部分的三元运算符 (1)为TRUE时(1)作为最终结果，否则(3)作为最终结果
echo '<br/>';
var_dump($x >= 1 ?: -1 ? 1 : 2); // int(1) 三元运算符是从左到右计算的
echo '<br/>';
var_dump(($x >= 1 ?: -1) ? 1 : 2); // int(1) 这样结构看起来更清楚
echo '<br/>';
```
* 对浮点数进行是否相等的比较是不合适的。

#### 错误控制运算符
使用错误控制运算符可以忽略任何错误，`php`目前只有一个错误控制运算符`@`。
```php
ini_set('display_errors', 'on');
error_reporting(E_ALL);

var_dump($hello);
// Notice: Undefined variable: hello in /Library/WebServer/Documents/index.php on line 5
// NULL 
echo '<br/>';

@var_dump($title);
// NULL 
echo '<br/>';

echo 'hello';
echo '<br/>';

// var_dump($hello) // 网页无法正常运作 mac os x
echo '<br/>';
// @var_dump($hello) // 网页无法正常运作 mac os x
echo '<br/>';

echo 'hello'; // hello
echo '<br/>';

ini_set('track_errors', 'on');
echo $php_errormsg; // Undefined variable: title
```
* 当开启了`track_errors`时，可以通过变量`$php_errormsg`获取最新的错误信息。
* `@`运算符在能阻止脚本运行的错误表达式上也是有效的，因此当用`@`来抑制一个会阻止脚本继续运行的错误时一个脚本会在我们在得不到任何信息的情况下卡死。

#### 执行运算符
使用执行运算符可以将要执行的内容作为`shell`命令来运行，`php`目前只有一个执行运算符(``)，即反引号。
```php
$ls_l = `ls -l`;
echo '<pre>';
var_dump($ls_l);
echo '</pre>';
// mac os x
/*
string(472) "total 112
-rwxrwxrwx  1 root       wheel   3726 Aug  9  2016 PoweredByMacOSX.gif
-rwxrwxrwx  1 root       wheel  31958 Aug  9  2016 PoweredByMacOSXLarge.gif
-rwxrwxrwx  1 root       wheel     87 Feb 25 07:40 index.php
-rw-r--r--@ 1 betterzfz  wheel    169 Feb 11 15:36 test.html
-rwxrwxrwx  1 root       wheel     45 Feb 11 15:37 test.html.en
-rwxrwxrwx  1 root       wheel     45 Feb 11 15:37 test.html.en~orig
-rw-r--r--  1 betterzfz  wheel    243 Feb 13 21:40 test.php
"
*/
```
* 执行运算符在打开了安全模式或者禁用了`shell_exec()`函数时是无效的。

#### 递增／递减运算符
在`php`中递增（操作数加1）运算符为`++`，分为前递增和后递增，递减（操作数减1）运算符为`--`，分为前递减和后递减。前递增和前递减会先对操作数进行递增或递减，然后再参加其它运算，后递增和后递减会先让操作数参加其它运算，然后再对操作数进行递增或递减。
```php
$x = 7;
echo $x++; // 7
echo '<br/>';
echo $x; // 8
echo '<br/>';
echo ++$x; // 9
echo '<br/>';
echo $x; // 9
echo '<br/>';
echo $x--; // 9
echo '<br/>';
echo $x; // 8
echo '<br/>';
echo --$x; // 7
echo '<br/>';
echo $x; // 7
echo '<br/>';
var_dump($y); // NULL
echo '<br/>';
var_dump(--$y); // NULL
echo '<br/>';
var_dump(++$y); // int(1)
echo '<br/>';
```
* 对`NULL`递减还是`NULL`，对`NULL`递增得到1。

#### 逻辑运算符
```php
$x = TRUE;
$y = FALSE;
var_dump($x and $y); // bool(false)  and 逻辑与 两个操作数都为真时结果为真
echo '<br/>';
var_dump($x and TRUE); // bool(true) 
echo '<br/>';
var_dump(FALSE and $y); // bool(false) 
echo '<br/>';
var_dump($x or $y); // bool(true)  or 逻辑或 两个操作数有一个为真时结果为真
echo '<br/>';
var_dump($x or TRUE); // bool(true) 
echo '<br/>';
var_dump(FALSE or $y); // bool(false) 
echo '<br/>';
var_dump($x xor $y); // bool(true)  or 逻辑异或 两个操作数不同时结果为真
echo '<br/>';
var_dump($x xor TRUE); // bool(false) 
echo '<br/>';
var_dump(FALSE xor $y); // bool(false) 
echo '<br/>';
var_dump(!$x ); // bool(false)  or 逻辑非 对操作数取反
echo '<br/>';
var_dump(!$y); // bool(true) 
echo '<br/>';
var_dump($x && $y); // bool(false)  && 逻辑与 两个操作数都为真时结果为真
echo '<br/>';
var_dump($x && TRUE); // bool(true) 
echo '<br/>';
var_dump(FALSE && $y); // bool(false) 
echo '<br/>';
var_dump($x || $y); // bool(true)  || 逻辑或 两个操作数有一个为真时结果为真
echo '<br/>';
var_dump($x || TRUE); // bool(true) 
echo '<br/>';
var_dump(FALSE || $y); // bool(false) 
echo '<br/>';
```
* `逻辑与`和`逻辑或`分别有两种不同形式运算符，但是优先级是不同的。`||`比`or`的优先级高，`&&`比`and`的优先级高。

#### 字符串运算符
在`php`中有两个字符串运算符，分别为`.`和`.=`。
```php
$hello = 'hello, world!';
$title = 'this is a title:';
echo $hello;
echo '<br/>';
echo $title;
echo '<br/>';
echo $title.$hello;
echo '<br/>';
$title = $title.$hello;
echo $title;
echo '<br/>';
$title .= $hello;
echo $title;
echo '<br/>';
```

#### 数组运算符
数组运算符用于对数组进行操作。
```php
$x = ['andy' => '刘德华', 'jack' => '张学友'];
$y = ['jack' => 'jackson', 'joe' => 'joe woo'];
$z = $x + $y; // + 联合 两个数组操作数的联合 把右边的数组元素附加到左边的数组后面，相同保留左边的忽略右边的。
echo '<pre>';
print_r($z);
echo '</pre>';
/*
Array
(
	[andy] => 刘德华
	[jack] => 张学友
	[joe] => joe woo
)
*/
$z = $y + $x;
echo '<pre>';
print_r($z);
echo '</pre>';
/*
Array
(
	[jack] => jackson
	[joe] => joe woo
	[andy] => 刘德华
)
*/
var_dump($x == $y); // bool(false) == 相等 两个数组操作数具有相同的键／值对
echo '<br/>';
$a = ['joe' => 'joe woo', 'andy' => '刘德华', 'jack' => 'jackson'];
var_dump($z == $a); // bool(true) 
echo '<br/>';
var_dump($z === $a); // bool(false) === 全等 两个数组操作数具有相同的键／值对并且顺序和类型都相同
echo '<br/>';
$b = ['jack' => 'jackson', 'joe' => 'joe woo', 'andy' => '刘德华'];
var_dump($z === $b); // bool(true) 
echo '<br/>';
var_dump($z != $a); // bool(false) != 不等 两个数组操作数不相等
echo '<br/>';
var_dump($z <> $b); // bool(false) <> 不等 两个数组操作数不相等
echo '<br/>';
var_dump($z !== $b); // bool(false) !== 不等 两个数组操作数不全等
echo '<br/>';
```

#### 运算符优先级
运算符优先级决定了运算的顺序。

| 运算符 | 结合方向 |
| ------ | ------ |
| ** | 右 |
| ++ -- ~ @ | 右 |
| ! | 右 |
| * / % | 左 |
| + - . | 左 |
| << >> | 左 |
| < <= > >= | 无 |
| == != === !== <> <=>(php7) | 无 |
| & | 左 |
| ^ | 左 |
| ｜ | 左 |
| && | 左 |
| ‖ | 左 |
| ? : | 左 |
| = += -= *= **= /= .= %= &= ｜= ^= <<= >>= | 右 |
| and | 左 |
| xor | 左 |
| or | 左 |
```php
$x = 2;
$y = 2;
var_dump(~$x ** $y); // int(-5)  
echo '<br/>';
var_dump(!$x--); // bool(false) 
echo '<br/>';
var_dump(!$x * $y); // int(0)
echo '<br/>';
var_dump(!($x * $y)); // bool(false) 
echo '<br/>';
echo 1 + $x * $y; // 3 
echo '<br/>';
echo 2 * $x ** $y; // 2 
echo '<br/>';
echo $x << 1 + $y; // 8 
echo '<br/>';
var_dump($x < 1 << $y); // 1 
echo '<br/>';
var_dump($x & 1 == $y); // int(0) 
echo '<br/>';
var_dump($y ^ $x & 1); // int(3) 
echo '<br/>';
var_dump($y | $x ^ 2); // int(3)   
echo '<br/>';
var_dump($y && $x | 2); // bool(true)    
echo '<br/>';
var_dump($y || $x && 0); // bool(true)     
echo '<br/>';
var_dump($x ? $y : 0 && 1); // int(2)      
echo '<br/>';
var_dump($x = 3 ? $y : 0); // int(2)      
echo '<br/>';
echo $x; // 2
echo '<br/>';
var_dump($x and $y = 0); // bool(false)
echo '<br/>';
var_dump($x xor $y and 0); // bool(true)
echo '<br/>';
var_dump(1 or 1 xor 1); // bool(true)
echo '<br/>';
```

#### 运算符的说明
* 运算符可以按照其能接受几个值进行分组，可分为一元运算符，二元运算符和三元运算符。
```php
$x = 3;
echo $x++; // 3
echo '<br/>';
echo $x; // 4
echo '<br/>';
// ++ -- ! ~ @等操作数只有一个操作数的运算符是一元运算符
echo $x ? : 9; // 4
echo '<br/>';
// ?:是唯一的可以有三个操作数的运算符，称为三元运算符
$y = 7;
$z = $x + $y;
echo $z; // 11
echo '<br/>';
// 可以有两个操作数的运算符称为二元运算符，除了一元运算符和三元运算符之外目前我们遇到过的都是二元运算符
```