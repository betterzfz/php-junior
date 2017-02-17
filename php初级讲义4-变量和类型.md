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
* 在`php`中数据总共有8中原始类型，分别为布尔型(`boolean`)，整形(`integer`)，浮点型(`float`)，字符串(`string`)，数组(`array`)，对象(`object`)，资源(`resource`)和无类型(`NULL`)。其中布尔型，整形，浮点型和字符串为四个标量类型，数组和对象是两个复合类型，资源和无类型是两个特殊类型。
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
echo print_r($data, true).'<br/>'; // 输出''
echo var_dump($data); // bool(false)
echo '<pre>';
echo print_r($data); // 输出1
echo '</pre>';
echo '<pre>';
echo print_r($data, true); // 输出''
echo '</pre>';
echo '<pre>';
echo var_dump($data); // 输出bool(false)
echo '</pre>';
```
* 整型包含了所有整数，整型数据可以用十进制，二进制(前置0b)，八进制(前置0)和十六进制(前置0x)表示，每种表示都可以有正负之分。整型数据的实例：
```php
$count = 10;
echo $count.'<br/>'; // 输出10
$count = -10;
echo $count.'<br/>'; // 输出-10
$count = 0b10;
echo $count.'<br/>'; // 输出2
$count = -0b10;
echo $count.'<br/>'; // 输出-2
$count = 010;
echo $count.'<br/>'; // 输出8
$count = -010;
echo $count.'<br/>'; // 输出-8
$count = 0x10;
echo $count.'<br/>'; // 输出16
$count = -0x10;
echo $count.'<br/>'; // 输出-16
$count = 0X10;
echo $count.'<br/>'; // 输出16
$count = -0X10;
echo $count.'<br/>'; // 输出-16
echo PHP_INT_MAX.'<br/>'; // 输出9223372036854775807，PHP_INT_MAX是预定义常量，表示整型数最大值
echo (PHP_INT_MAX + 1).'<br/>'; // 输出9.2233720368548E+18
```
* 浮点型就是浮点数，也被称作双精度数(`double`)或实数(`real`)，就是带有小数点的数字，有的浮点数在计算机中是没有办法精确表示的。浮点型数据的实例：
```php
$number = 3.14;
echo $number.'<br/>'; // 输出3.14
$number = 3.14e2; // 科学计数法
echo $number.'<br/>'; // 输出314
$number = 3.14e-2; // 科学计数法
echo $number.'<br/>'; // 输出0.0314
$number = 3.14E2; // 科学计数法
echo $number.'<br/>'; // 输出314
$number = 3.14E-2; // 科学计数法
echo $number.'<br/>'; // 输出0.0314
$number = 0.5;
echo $number.'<br/>'; // 输出0.5
echo var_dump($number).'<br/>'; // 输出float(0.5)
echo print_r($number).'<br/>'; // 输出0.51
echo print_r($number, true).'<br/>'; // 输出0.5
echo '<pre>';
echo var_dump($number); // 输出float(0.5)
echo '</pre>';
echo '<pre>';
echo print_r($number); // 输出0.51
echo '</pre>';
echo '<pre>';
echo print_r($number, true); // 输出0.5
echo '</pre>';
/*
5 101
5 ／ 2 1
2 ／ 2 0
1 ／ 2 1
0
0.7 0.101100110011001100
0.7 * 2 1
0.4 * 2 0
0.8 * 2 1
0.6 * 2 1
0.2 * 2 0
0.4
通过二进制转换可以理解下面的输出
*/
echo floor((0.1 + 0.7) * 10); // 输出7
```
* 字符串由一系列字符组成，起始和结束位置分别有一个定界符，可能是`'`, `"`, `heredoc语法结构`或`nowdoc语法结构`。字符串数据实例：
```php
$title = 'this is a title';
echo $title.'<br/>'; // 输出'this is a title'
$title = 'this is a title named "hello, world!"';
echo $title.'<br/>'; // 输出'this is a title named "hello, world!"'
// $title = 'this is a title named 'hello, world!''; // localhost 网页无法正常运作
$title = 'this is a title named \'hello, world!\'';
echo $title.'<br/>'; // 输出"this is a title named 'hello, world!'"
$title = 'this is a title named \hello, world!';
echo $title.'<br/>'; // 输出'this is a title named \hello, world!'
$title = 'this is a title named \ hello, world!';
echo $title.'<br/>'; // 输出'this is a title named \ hello, world!'
$title = 'this is a title named \\ hello, world!';
echo $title.'<br/>'; // 输出'this is a title named \ hello, world!'

$title = "this is a title";
echo $title.'<br/>'; // 输出'this is a title'
// $title = "this is a title named "hello, world!""; // localhost 网页无法正常运作
$title = "this is a title named 'hello, world!'";
echo $title.'<br/>'; // 输出"this is a title named 'hello, world!'"
$title = "this is a title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is a title named "hello, world!"'
$title = "this is a title \named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is a title amed "hello, world!"', 在mac os x下的结果，其它平台可能不同
$title = "this is a \title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is a itle named "hello, world!"', 在mac os x下的结果，其它平台可能不同
$title = "this is a \r title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is a title named "hello, world!"', 在mac os x下的结果，其它平台可能不同
$title = "this is a \v title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is a  title named "hello, world!"', 在mac os x下的结果，其它平台可能不同
$title = "this is \a title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is \a title named "hello, world!"'
$title = "this is \\a title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is \a title named "hello, world!"'
$title = "this is \ a title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is \ a title named "hello, world!"'
$title = "this is \\ a title named \"hello, world!\"";
echo $title.'<br/>'; // 输出'this is \ a title named "hello, world!"'

$title = 'this is a title \named "hello, world!"';
echo $title.'<br/>'; // 输出'this is a title \named "hello, world!"'
$title = 'this is a \title named "hello, world!"';
echo $title.'<br/>'; // 输出'this is a \title named "hello, world!"'
$title = 'this is a \r title named "hello, world!"';
echo $title.'<br/>'; // 输出'this is a \r title named "hello, world!"'
$title = 'this is a \v title named "hello, world!"';
echo $title.'<br/>'; // 输出'this is a \v title named "hello, world!"'
$title = 'this is a title named \"hello, world!\"';
echo $title.'<br/>'; // 输出'this is a title named \"hello, world!\"'

$title = "this is a title named \'hello, world!\'";
echo $title.'<br/>'; // 输出'this is a title named \'hello, world!\''

// 在双引号包围的字符串中，php会对变量和一些特殊字符(\n,\r,\t,\v,\\,\$等)进行解析
$hello = 'hello, world!';
echo $hello.'<br/>'; // 输出'hello, world!'
echo 'this is a title named $hello'.'<br/>'; // 输出'this is a title named $hello'
echo "this is a title named $hello".'<br/>'; // 输出'this is a title named hello, world!'
echo 'this is a title named \$hello'.'<br/>'; // 输出'this is a title named \$hello'
echo "this is a title named \$hello".'<br/>'; // 输出'this is a title named $hello'

    /*
    heredoc结构以<<<作为运算符，后面接上标识符，标识符的命名规范同变量名一样，换行后接字符串值，最后另起一行放置<<<后定义的标识符作结尾，这一行除了标识符和可能存在的分号外不能包含任何其它字符。
    heredoc结构和双引号一样都可以对变量和特殊字符进行解析。
    */
    $title = <<<TITLE
        this is a title
TITLE;
    echo $title.'<br/>'; // 输出'this is a title'
    /*$title = <<<TITLE
        this is a title
TITLE;  */ // 网页无法正常运作
    $title = <<<TITLE
        this is a title

TITLE;
    echo $title.'<br/>'; // 输出'this is a title '
    /*$title = <<<TITLE
        this is a title
TITLE; */ // 网页无法正常运作
    /*$title = <<<TITLE
        this is a title
    TITLE; // 网页无法正常运作
    */
    /*$title = <<<TITLE
        this is a title
 TITLE; // 网页无法正常运作
    */
    $title = <<<TITLE
        "this is a title"
TITLE;
    echo $title.'<br/>'; // 输出'"this is a title"'
    $title = <<<TITLE
        'this is a title'
TITLE;
    echo $title.'<br/>'; // 输出"'this is a title'"
    $title = <<<title
        \'this is a title\'
title;
    echo $title.'<br/>'; // 输出"\'this is a title\'"
    $title = <<<title
        \"this is a title\"
title;
    echo $title.'<br/>'; // 输出'\"this is a title\"'
    /*$title = <<<title
        this is a title
TITLE;*/ // 网页无法正常运作
    $title = <<<title
        this is a title \named "hello, world!"
title;
    echo $title.'<br/>'; // 输出'this is a title amed "hello, world!"', 在mac os x下的结果，其它平台可能不同
    $title = <<<title
        this is a \title named \"hello, world!\"
title;
    echo $title.'<br/>'; // 输出'this is a itle named \"hello, world!\"', 在mac os x下的结果，其它平台可能不同
    $title = <<<title
        this is a \r title named \"hello, world!\"
title;
    echo $title.'<br/>'; // 输出'this is a title named \"hello, world!\"', 在mac os x下的结果，其它平台可能不同
    $title = <<<title
        this is a \v title named \"hello, world!\"
title;
    echo $title.'<br/>'; // 输出'this is a  title named \"hello, world!\"', 在mac os x下的结果，其它平台可能不同
    $title = <<<title
        this is \a title named \"hello, world!\"
title;
    echo $title.'<br/>'; // 输出'this is \a title named \"hello, world!\"'
    $title = <<<title
        this is \\a title named \"hello, world!\"
title;
    echo $title.'<br/>'; // 输出'this is \a title named \"hello, world!\"'
    $title = <<<title
        this is \ a title named \"hello, world!\"
title;
    echo $title.'<br/>'; // 输出'this is \ a title named \"hello, world!\"'
    $title = <<<title
        this is \\ a title named \"hello, world!\"
title;
    echo $title.'<br/>'; // 输出'this is \ a title named \"hello, world!\"'
    $title = <<<title
        this is a title named \'hello, world!\'
title;
    echo $title.'<br/>'; // 输出"this is a title named \'hello, world!\'"
    $title = <<<title
        this is a title named $hello
title;
    echo $title.'<br/>'; // 输出"this is a title named hello, world!"
    $title = <<<title
        this is a title named \$hello
title;
    echo $title.'<br/>'; // 输出"this is a title named $hello"
    $title = <<<"title"
        this is a title named \$hello
title;
    echo $title.'<br/>'; // 输出"this is a title named $hello"
    $title = <<<'title'
        this is a title named \$hello
title;
    echo $title.'<br/>'; // 输出"this is a title named \$hello"
    $title = <<<'title'
        this is a title named $hello
title;
    echo $title.'<br/>'; // 输出"this is a title named $hello"
    $title = <<<'title'
        this is \a \\ \ \title \named $hello
title;
    echo $title.'<br/>'; // 输出"this is \a \\ \ \title \named $hello"

    // nowdoc语法结构和heredoc类似，区别是不会对特殊字符进行解析，开始处的标识符用单引号引起来。
    $doc = <<<'DOC'
    this is a title,
    this is a paragraph.
DOC;
    echo $doc.'<br/>'; // 输出'this is a title, this is a paragraph'
    $doc = <<<'DOC'
    this is a title,
    this is a paragraph
DOC;
    echo $doc.'<br/>';
    $title = <<<'DOC'
        this is a title
DOC;
    echo $title.'<br/>'; // 输出'this is a title'
    $title = <<<'DOC'
        this is a title named "hello, world!"
DOC;
    echo $title.'<br/>'; // 输出'this is a title named "hello, world!"'
    $title = <<<'DOC'
        this is a title named 'hello, world!'
DOC;
    echo $title.'<br/>'; // 输出"this is a title named 'hello, world!'"
    $title = <<<'DOC'
        this is a title named \'hello, world!\'
DOC;
    echo $title.'<br/>'; // 输出"this is a title named \'hello, world!\'"
    $title = <<<'DOC'
        this is a \r \v \title \named \\  \ \hello, world!
DOC;
    echo $title.'<br/>'; // 输出'this is a \r \v \title \named \\ \ \hello, world!'
    $title = <<<'DOC'
        this is a title named \"hello, world!\"
DOC;
    echo $title.'<br/>'; // 输出'this is a title named \"hello, world!\"'
    $hello = 'hello, world!';
    $title = <<<'DOC'
        this is a title named $hello
DOC;
    echo $title.'<br/>'; // 输出'this is a title named $hello'
    $title = <<<'DOC'
        this is a title named \$hello
DOC;
    echo $title.'<br/>'; // 输出'this is a title named \$hello'
    /*$title = <<<'DOC'
        this is a title named \$hello
doc;*/ // 网页无法正常运作
```