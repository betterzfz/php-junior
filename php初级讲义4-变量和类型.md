#### 变量
* 为了实现程序逻辑和数据的复用在编程语言中引入了变量。
* `php`变量以美元符号`$`后面跟随数字，字母和下划线组成的变量名构成，变量名区分大小写且以字母或者下划线开头。
* 以下是一些变量的实例：
```php
$title = 'hello, world!';
echo $title; // 输出'hello, world!'
$number = 1;
echo $number; // 输出1
$孙悟空 = '风一般的男子'; // 汉字可以用作变量名
echo $孙悟空; // 输出'风一般的男子'
$_name = '孙悟空';
echo $_name; // 输出'孙悟空'
$1name = 'tom'; // parse error, expecting `"variable (T_VARIABLE)"' or `'$''
```
* `=`为赋值运算符，表示将右边的数据赋值给左边的符号(如变量)，一个变量可以赋值给另一个变量，如：
```php
$title = 'hello, world!';
echo $title; // 输出'hello, world!'
$subject = $title;
echo $subject; // 输出'hello, world!'
```
* 可以声明一个变量而不赋值，之后再对其进行赋值，如：
```php
$title;
echo $title; // 输出''
$title = 'hello, world!';
echo $title; // 输出'hello, world!'
```
* `php`中存在`可变变量`这个概念，这样可以动态得设置和使用变量名，如：
```php
$title = 'hello';
echo $title.'<br/>'; // 输出'hello'
$$title = 'world';
echo $hello;  // 输出'world
```
* `.`在`php`中可以用于字符拼接。
* `<br/>`是`html`的一个标签，用于在网页上进行换行。

#### 类型
* 在`php`中数据总共有8中原始类型，分别为布尔型(boolean)，整形(integer)，浮点型(float)，字符串(string)，数组(array)，对象(object)，资源(resource)和无类型(NULL)。其中布尔型，整形，浮点型和字符串为四个标量类型，数组和对象是两个复合类型，资源和无类型是两个特殊类型。
* 布尔型数据只有两个，`TRUE`和`FALSE`，不区分大小写，非真即假，常用做逻辑判断。布尔数据的实例：
```php
$data = TRUE;
echo $data.'<br/>'; // 输出1
$data = true;
echo $data.'<br/>'; // 输出1
$data = True;
echo $data.'<br/>'; // 输出1
$data = FALSE;
echo $data.'<br/>'; // 输出''
echo print_r($data).'<br/>'; // 输出1
echo var_dump($data); // bool(false)
echo '<pre>';
echo print_r($data); // 输出1
echo '</pre>';
```