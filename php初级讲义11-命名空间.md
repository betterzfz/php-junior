#### 命名空间的概念
命名空间是一种封装事物的方法。

- 命名空间用`namespace`关键字来声明。
```php
class Person {}

$stone = new Person;
echo '<pre>';
print_r($stone);
echo '</pre>';
/*
Person Object
(
)
*/
```
```php
namespace name\space;

class Person {}

$stone = new Person;
echo '<pre>';
print_r($stone);
echo '</pre>';

$tom = new \name\space\Person;
echo '<pre>';
print_r($tom);
echo '</pre>';

function say_hello() {}

const COUNT = 1;

var_dump(COUNT);
echo '<br/>';
var_dump(\name\space\COUNT);
echo '<br/>';
var_dump(namespace\COUNT);
echo '<br/>';
var_dump(__NAMESPACE__);
echo '<br/>';
var_dump(__NAMESPACE__.'\COUNT');
echo '<br/>';
echo constant(__NAMESPACE__.'\COUNT');
/*
name\space\Person Object
(
)

name\space\Person Object
(
)

int(1)
int(1)
int(1)
string(10) "name\space"
string(16) "name\space\COUNT"
1
*/
```
- 以`PHP`或`php`为名或开头的命名空间被保留作为语言内核使用。
- 只有类，接口，函数和常量受命名空间的影响。
- 除了使用`declare`关键字以`declare(encoding='...')`方式指定脚本编码方式之外任何代码都不能出现在命名空间声明之前。
```php
<html>
<?php
    namespace MyNamespace;
// Fatal error: Namespace declaration statement has to be the very first statement in the script in
```
- 同一命名空间可以被定义在多个文件中。
- `php`允许创建形如`Multi\Level\Namespace`这样的多层命名空间。
- 同一个文件中可以包含多个命名空间，但是不提倡这么做，这种情形主要用于将多个php脚本合并到一个文件中。
```php
namespace MyNamespace;
const COUNT = 1;
var_dump(COUNT);
echo '<br/>';

namespace YourNamespace;
CONST COUNT = 2;
var_dump(COUNT);

/*
int(1) 
int(2)
*/

// 以上属于是单个文件多个命名空间的简单组合语法形式
```
```php
namespace MyNamespace {
    const COUNT = 1;
    var_dump(COUNT);
    echo '<br/>';
}

namespace YourNamespace {
    CONST COUNT = 2;
    var_dump(COUNT);
}

/*
int(1) 
int(2)
*/

// 以上属于是单个文件多个命名空间的大括号语法形式，比简单组合语法形式更值得推荐
```
- 将命名空间中的代码和全局非命名空间中的代码组合在一起时只能使用大括号语法形式，全局代码必须使用不带名称的`namespace`语句加上大括号括起来。
```php
namespace MyProject {
    function hello()
    {
        echo 'hello';
    }
    hello(); // hello
    echo '<br/>';
}

namespace {
    // hello(); // Fatal error: Call to undefined function hello() ini
    MyProject\hello(); // hello
}
```
#### 命名空间的使用
命名空间中的元素有三种使用方式
- 非限定名称（不包含前缀的名称）：如果元素包含在命名空间中则会被解析成当前命名空间中的元素，如果当前命名空间中没有定义该元素则该元素会被认为是全局的，如果使用元素的代码不在任何命名空间中则会被认为是全局的。
- 限定名称（包含前缀的名称）：如果在命名空间中使用元素，则当前的命名空间会被加在限定名称前作为最终要使用的元素，如果在全局作用域使用元素，则元素按照指定的限定名称使用。
- 完全限定名称（包含了全局前缀操作符的名称）：这种情况下元素就按照指定的名称进行访问。
```php
// Person.php
namespace Project\App\Model;

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App\Model';
        echo '<br/>';
    }
}
```
```php
namespace Project\App;

require_once 'Person.php';

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App';
        echo '<br/>';
    }
}

Person::hello(); // hello in Project\App

Model\Person::hello(); // hello in Project\App\Model

\Project\App\Person::hello(); // hello in Project\App

\Project\App\Model\Person::hello(); // hello in Project\App\Model

echo \strlen('hello'); // 5
echo '<br/>';
echo \PHP_INT_MAX; // 9223372036854775807
echo '<br/>';
echo strlen('hello'); // 5
echo '<br/>';
echo PHP_INT_MAX; // 9223372036854775807
echo '<br/>';
```
- 在命名空间中使用动态类名称、常量名称或函数名称时不能使用非限定名称。
```php
// Person.php
namespace Project\App\Model;

const COUNT = 'this is a constant in Project\App\Model';

function test()
{
    echo 'this is a function in Project\App\Model';
    echo '<br/>';
}

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App\Model';
        echo '<br/>';
    }
}
```
```php
namespace Project\App;

require_once 'Person.php';

const COUNT = 'this is a constant in Project\App';

function test()
{
    echo 'this is a function in Project\App';
    echo '<br/>';
}

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App';
        echo '<br/>';
    }
}

echo COUNT; // this is a constant in Project\App
echo '<br/>';
$count = 'COUNT';
echo constant($count); // Warning: constant(): Couldn't find constant COUNT in
echo '<br/>';
$count = 'Project\App\COUNT';
echo constant($count); // this is a constant in Project\App
echo '<br/>';
test(); // this is a function in Project\App
$function_name = 'test';
// $function_name(); // Fatal error: Call to undefined function test() in
$function_name = 'Project\App\Model\test';
$function_name(); // this is a function in Project\App\Model
Person::hello(); // hello in Project\App
$class_name = 'Person';
//$class_name::hello(); // Fatal error: Class 'Person' not found in
$class_name = '\Project\App\Person';
$class_name::hello(); // hello in Project\App
```
- 通过预定义常量`__NAMESPACE__`可以获取当前命名空间的名称。
```php
var_dump(__NAMESPACE__); // string(0) ""
```
```php
namespace App\Http\Controller;

echo __NAMESPACE__; // App\Http\Controller
```
- 通过类似于类的`self`操作符的关键字`namespace`可以显式地访问当前命名空间或者子命名空间中的元素。
```php
// Person.php
namespace Project\App\Model;

const COUNT = 'this is a constant in Project\App\Model';

function test()
{
    echo 'this is a function in Project\App\Model';
    echo '<br/>';
}

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App\Model';
        echo '<br/>';
    }
}
```
```php
namespace Project\App;

require_once 'Person.php';

const COUNT = 1;

namespace\Model\test(); // this is a function in Project\App\Model

echo namespace\COUNT; // 1
```
- 命名空间允许通过别名引用或导入外部的完全限定名称。
```php
// Person.php
namespace Project\App\Model;

const COUNT = 'this is a constant in Project\App\Model';

function test()
{
    echo 'this is a function in Project\App\Model';
    echo '<br/>';
}

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App\Model';
        echo '<br/>';
    }
}

class Programmer extends Person
{
    public static function code()
    {
        echo 'I am coding...';
        echo '<br/>';
    }
}
```
```php
namespace Project\App;
ini_set('display_errors', 'on');
error_reporting(E_ALL);
require_once 'Person.php';

use Project\App\Model\Programmer as Prog;
Prog::code(); // I am coding...

use Project\App\Model\Person; // 词句与use Project\App\Model\Person as Person等价;
Person::hello(); // hello in Project\App\Model

use function Project\App\Model\test; // php5.6+
test(); // this is a function in Project\App\Model

use const Project\App\Model\COUNT; // php5.6+
echo COUNT; // this is a constant in Project\App\Model
echo '<br/>';

use Project\App as App;
App\Model\test(); // this is a function in Project\App\Model
```
- 对命名空间中的名称来说，前导的反斜杠是不必要的也是不推荐的，因为导入名称是完全限定的，不会根据当前的命名空间作相对解析。
- `php`支持在一行中使用多个`use`。
```php
// Person.php
namespace Project\App\Model;

const COUNT = 'this is a constant in Project\App\Model';

function test()
{
    echo 'this is a function in Project\App\Model';
    echo '<br/>';
}

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App\Model';
        echo '<br/>';
    }
}

class Programmer extends Person
{
    public static function code()
    {
        echo 'I am coding...';
        echo '<br/>';
    }
}
```
```php
namespace Project\App;
ini_set('display_errors', 'on');
error_reporting(E_ALL);
require_once 'Person.php';

use Project\App\Model\Person, Project\App\Model\Programmer as Prog;

Person::hello(); // hello in Project\App\Model
Prog::code(); // I am coding...
```
- 导入操作是在编译时执行的，而动态的类名称、函数名称和常量名称不是的。
```php
// Person.php
namespace Project\App\Model;

const COUNT = 'this is a constant in Project\App\Model';

function test()
{
    echo 'this is a function in Project\App\Model';
    echo '<br/>';
}

class Person
{
    public static function hello()
    {
        echo 'hello in Project\App\Model';
        echo '<br/>';
    }
}

class Programmer extends Person
{
    public static function code()
    {
        echo 'I am coding...';
        echo '<br/>';
    }
}
```
```php
namespace Project\App;
ini_set('display_errors', 'on');
error_reporting(E_ALL);
require_once 'Person.php';

use Project\App\Model\Person;
Person::hello(); // hello in Project\App\Model
$class_name = 'Person';
$class_name::hello(); // Fatal error: Class 'Person' not found in
```
- 导入操作只影响非限定和限定名称。完全限定名称是确定的，不受导入影响。