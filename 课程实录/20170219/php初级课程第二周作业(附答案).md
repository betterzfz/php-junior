* 定义一个字符串变量，并将其在另一个字符串中输出具体值，请分别用两种方式实现。
```php
    $hello = 'hello, world!';
    $title = "this is a title named $hello";
    echo $title.'<br/>';
    $title = <<<TITLE
        this is a title named $hello
TITLE;
    echo $title;
```
* 给定的一个十进制数3244，请分别将其转换成为二进制，八进制和十六进制。
```php
十进制转二进制采用除二逆向取余法
2 3244 0
2 1622 0
2  811 1
2  405 1
2  202 0
2  101 1
2   50 0
2   25 1
2   12 0
2    6 0
2    3 1
2    1 1
     0
十进制数3244转换成为二进制为：110010101100
十进制数转八进制可以使用除八逆向取余法，不过还有一种更好的方式就是通过二进制转换
3244的二进制为 110010101100，从左到右3个数字为一组 110 010 101 100，得到四组数字分别转化成为八进制数字
二进制 十进制 八进制
110       6      6
010       2      2
101       5      5
100       4      4
得到八进制数为 06254
十进制数转十六进制可以使用除十六逆向取余法，不过还有一种更好的方式就是通过二进制转换
3244的二进制为 110010101100，从左到右4个数字为一组 1100 1010 1100，得到四组数字分别转化成为十六进制数字
二进制 十进制 十六进制
1100      12       c
1010      10       a
1100      12       c
得到八进制数为 0xcac
````
* 请定义一个变量，给这个变量赋予一个值，然后以这个变量的值作为变量名定义另一个变量并赋值然后打印输出。
```php
$title = 'hello';
$$title = 'hello, world!';
echo $hello;
```
或
```php
$title = 'hello';
$hello = 'hello, world!';
echo $$title;
```
* 写出`php`的八种数据类型。
布尔型(boolean)，整形(integer)，浮点型(float)，字符串(string)，数组(array)，对象(object)，资源(resource)和无类型(NULL)
* 对于给定的二进制数1000111101，将其转换成八进制和十六进制数。
可以通过十进制作为中间值进行转换，这里直接进行转换
转换成八进制
1 000 111 101 => 1 0 7 5 => 01075
转换成十六进制
10 0011 1101 => 2 3 13 => 0x23d
* 使用四种方式定义字符串'hello, world!'并在浏览器中进行打印输出。
```php
echo 'hello, world!'.'<br/>';
echo "hello, world!".'<br/>';
$hello = <<<hello
    hello, world!
hello;
echo $hello.'<br/>';
$hello = <<<'HELLO'
    hello, world!
HELLO;
echo $hello.'<br/>';
```
* 请说明单引号与双引号在作为字符串包围标记时的区别。
双引号会对内部的特殊字符和变量进行解析而单引号不会。
* 请用两种方式定义一个常量并将其进行输出。
```php
define('TITLE', 'this is a title.');
echo TITLE.'<br/>';
const HELLO = 'hello, world!';
echo HELLO;
```
* 请定义一个变量用来描述香港四大天王的姓名信息，并分别以不考虑类型和考虑类型的方式输出这个变量。
```php
$four_king = ['刘德华', '张学友', '黎明', '郭富城'];
echo '<pre>';
print_r($four_king);
echo '</pre>';
echo '<pre>';
var_dump($four_king);
echo '</pre>';
```
* 请定义一个至少包含4个元素的关联数组，然后分别打印输出数组中元素的值。
```php
$four_king = ['andy' => '刘德华', 'jack' => '张学友', 'leon' => '黎明', 'aaron' => '郭富城'];
echo $four_king['andy'].'<br/>';
echo $four_king['jack'].'<br/>';
echo $four_king['leon'].'<br/>';
echo $four_king['aaron'].'<br/>';
```
* 请定义一个至少包含4个元素的数组，然后修改第三个元素的值并增加一个有指定键和指定值的元素，最后打印输出之。
```php
$stars = ['andy' => '刘德华', 'jack' => '张学友', 'leon' => '黎明', 'aaron' => '郭富城'];
$stars['leon'] = '谭咏麟';
$stars['ka'] = '黄家驹';
echo '<pre>';
print_r($stars);
echo '</pre>';
```
* 请定义一个多维数组尽可能详细您的个人信息，最后将这个信息打印输出到浏览器中。
```php
$personal_info = [
    'name' => '卓浩',
    'height' => '176cm',
    'weight' => '65kg',
    'skills' => ['php', 'mysql', 'html', 'css', 'javascript'],
    'feature' => [
        'hobby' => ['program', 'film'],
    ],
];
echo '<pre>';
print_r($personal_info);
echo '</pre>';
```