#### 类和对象
类是对一类事物的描述，对象是类的实例。在面向对象编程思想中一切事物都是对象，类和对象是面向对象编程的重要组成部分。

#### 类的定义
```php
class Person
{
    public $name;

    function eat(){
        echo 'I am eating';
    }

    function self_introduce(){
        echo 'my name is '.$this->name;
    }

    function get_this(){
        if (isset($this)) {
            echo 'class is '.get_class($this);
        } else {
            echo 'there is no $this';
        }
    }
}

class Book
{
    function get_that(){
        Person::get_this();
    }
}

$tom = new Person();
$tom->name = 'tom';
$tom->eat(); // I am eating
echo '<br/>';
$tom->self_introduce(); // my name is tom
echo '<br/>';

$tom->get_this(); // class is Person
echo '<br/>';
Person::get_this();
// Deprecated: Non-static method Person::get_this() should not be called statically in D:\www\test\test1.php on line 39
// there is no $this
echo '<br/>';

$three_country = new Book;
$three_country->get_that();
// Deprecated: Non-static method Person::get_this() should not be called statically in D:\www\test\test1.php on line 26
// there is no $this
echo '<br/>';

Book::get_that();
// Deprecated: Non-static method Book::get_that() should not be called statically in D:\www\test\test1.php on line 50
// Deprecated: Non-static method Person::get_this() should not be called statically in D:\www\test\test1.php on line 26
// there is no $this

$class_name = 'Person';
$jack = new $class_name();
echo '<pre>';
print_r($jack);
echo '</pre>';
/*
Person Object
(
    [name] => 
)
*/
$lucy = $jack;
$lily = &$jack;
$jack = null;
echo '<pre>';
var_dump($jack);
echo '</pre>';
echo '<pre>';
var_dump($lucy);
echo '</pre>';
echo '<pre>';
var_dump($lily);
echo '</pre>';
/*
NULL
object(Person)#1 (1) {
  ["name"]=>
  NULL
}
NULL
*/
$jim = new Person();
$andy = new $jim;
echo '<pre>';
print_r($andy);
echo '</pre>';
echo '<pre>';
var_dump($jim == $andy);
echo '</pre>';
echo '<pre>';
var_dump($jim === $andy);
echo '</pre>';
$john = new Person();
echo '<pre>';
var_dump($jim == $john);
echo '</pre>';
echo '<pre>';
var_dump($jim === $john);
echo '</pre>';
/*
Person Object
(
    [name] => 
)
bool(true)
bool(false)
bool(true)
bool(false)
*/

class Programmer extends Person
{
    function self_introduce(){
        parent::self_introduce();
        echo '<br/>';
        echo 'I am a programmer, my name is '.$this->name;
    }
}

$hanks = new Programmer();
$hanks->name = 'hanks';
$hanks->self_introduce();
// my name is hanks
// I am a programmer, my name is hanks
```
- 类的定义以关键字`class`开头，后面跟着类名，然后是一对大括号包围的类结构。
- 一个合法的类名由字母数字和下划线组成且不能以数字开头。
- 类名通常用大驼峰法命名，花括号都独占一行，这些不是必须的。
- 类结构中可以包含变量，常量和函数，在类中的变量是类的属性，常量是类常量，函数是类的方法。
- `$this`是一个可以在类内部使用的伪变量，是一个到主叫对象的引用。
- 函数`get_class()`用来获取指定对象所属的类。
- `::`是范围解析操作符，可以用于在类外访问类的方法。
- 通过`new`关键字来实例化一个类成为对象。
- `->`是对象运算符，可以用来访问对象的属性和方法。
- 类名可以使用变量表示。
- 可以使用`extends`关键字指定一个类继承自另一个类，继承的类就有了被继承类的属性和方法。在`php`中一个类只能继承自一个基类。继承的属性和方法可以通过同名属性和方法去覆盖，父类中使用`final`关键字声明的方法不能覆盖，可以使用`parent::`来访问父类中被覆盖的属性和方法。覆盖父类方法时，除了构造函数，其它的方法的参数列表需要和父类保持一致。

#### 类的属性
类中的成员变量就是类的属性。属性的声明要以关键字`public`, `protected`或`private`开头，后面跟着一个变量声明，作为属性的变量可以进行初始化，`public`, `protected`或`private`表示了属性的可见性。
```php
$shanghai = 'shanghai';
const JIANGSU = 'jiangsu';

class Person
{
    // $name; // Parse error: syntax error, unexpected '$name' (T_VARIABLE), expecting function (T_FUNCTION) or const (T_CONST) in
    var $name;
    public $sex;
    public $age = 12;
    public $count = 1 + 2;
    public $introduction = 'I am a '.'programmer';
    public $motto = <<<EOD
	impossible is nothing
EOD;
    // public $hello = self::return_string(); // Fatal error: Constant expression contains invalid operations in
    // public $city = $shanghai; // Fatal error: Constant expression contains invalid operations in
    public static $new_name = 'another name';
    // public $another_name = self::$new_name; // Fatal error: Constant expression contains invalid operations
    public $province = JIANGSU;
    public $area = ['putuo', 'minhang'];
    public $mobile = <<<'EOD'
	11111111111
EOD;

    static function return_string(){
    	return 'hello';
    }

    function return_hello(){
    	return self::return_string();
    }

    function return_shanghai(){
    	return $shanghai;
    }

    function return_new_name(){
    	return self::$new_name;
    }
}

$tom = new Person();
echo '<pre>';
var_dump($tom->name); // NULL
echo '</pre>';
echo '<pre>';
var_dump($tom->sex); // NULL
echo '</pre>';
echo $tom->age; // 12
echo '<br/>';
echo $tom->introduction; // I am a programmer
echo '<br/>';
echo $tom->motto; // impossible is nothing
echo '<br/>';
echo Person::return_string(); // hello
echo '<br/>';
echo $tom->return_hello(); // hello
echo '<br/>';
echo $tom->return_shanghai(); // Notice: Undefined variable: shanghai in
echo '<br/>';
echo $tom->return_new_name(); // another name
echo '<br/>';
echo $tom->count; // 3
echo '<br/>';
echo JIANGSU; // jiangsu
echo '<br/>';
echo $tom->province; // jiangsu
echo '<br/>';
echo ANHUI;
// Notice: Use of undefined constant ANHUI - assumed 'ANHUI' in
// ANHUI
echo '<br/>';
echo '<pre>';
print_r($tom->area);
echo '</pre>';
/*
Array
(
    [0] => putuo
    [1] => minhang
)
 */
echo '<br/>';
echo $tom->mobile; // 11111111111
```
- 可以通过对象运算符`->`访问非静态属性，静态属性要通过`::`来访问。
- 可以通过关键字`var`来声明属性，这是`php5`之前用法，在`php5`的某些版本这种用法被废弃并会产生报错，如果没有使用`public`, `protected`或`private`等修饰符，仅使用`var`声明的变量会被认为是`public`的。
- 类中的关键字`self`表示类本身。

#### 类常量
在类中定义的常量被称为类常量。
```php
$count = 2;
class Person
{
	const head_number = 1;
	// define(eyes_number, 2); // Parse error: syntax error, unexpected 'define' (T_STRING), expecting function (T_FUNCTION) or const (T_CONST) in
	const EYES_NUMBER = 2;
	// const 1hands_number = 1; // Parse error: syntax error, unexpected '1' (T_LNUMBER) in
	const _handsnumber2 = 2;
	// const hands_@number = 3; // Parse error: syntax error, unexpected '@', expecting '=' in
	// const hands_number; // Parse error: syntax error, unexpected ';', expecting '=' in
	const hands_number = 1 + 1;
	public static $count = 2;
	// const legs_number = $count; // Fatal error: Constant expression contains invalid operations in
	// const legs_number = self::$count; // Fatal error: Constant expression contains invalid operations in
	// const legs_number = self::return_count(); // Fatal error: Constant expression contains invalid operations in
	const hello = <<<EOD
		hello
EOD;
	const world = <<<'EOD'
		world
EOD;
	const arr = [0, 1, 2];

	static function return_count(){
		return self::$count;
	}

	function return_head_number(){
		return self::head_number;
	}
}

echo Person::head_number; // 1
echo '<br/>';
// echo Person::eyes_number; // Fatal error: Uncaught Error: Undefined class constant 'eyes_number' in
// echo Person::eyes_number; // Fatal error: Uncaught Error: Undefined class constant 'eyes_number' in
echo Person::EYES_NUMBER; // 2
echo '<br/>';
echo Person::_handsnumber2; // 2
echo '<br/>';
echo Person::hands_number; // 2
echo '<br/>';
$tom = new Person;
echo $tom->return_head_number(); // 1
$class_name = 'Person';
echo '<br/>';
echo $class_name::head_number; // 1
echo '<br/>';
echo $tom::head_number; // 1
echo '<br/>';
// echo $tom->head_number; // Notice: Undefined property: Person::$head_number in
echo $tom::hello; // hello
echo '<br/>';
echo $tom::world; // world
echo '<br/>';
echo '<pre>';
print_r($tom::arr);
echo '</pre>';
/*
Array
(
    [0] => 0
    [1] => 1
    [2] => 2
)
*/
```
- 类常量必须是一个定值，不能是变量，类属性或是函数调用结果。
- 可以通过`const`关键字来定义类常量但是不可以使用`define()`函数。
- 类常量不用`$`符作为前引，类常量名由数字字母下划线构成但是不能以数字开头，类常量名区分大小写。
- 常量声明时就要初始化值。
- 在类外部访问常量可以听过类或者对象使用`::`运算符来进行，在类内部访问使用常量可以通过`self::`来进行，`self`表示类本身。

#### 类的继承
继承是面向对象编程时实现代码复用的重要途径，继承会影响到类与类，对象与对象之间的关系。通过继承可以让一个类拥有和扩展另一个类的功能，前者被称为子类，后者被称为父类或基类。
```php
class Person
{
	public $name = 'stone';
	protected $sex;
	private $age;

	public function return_name(){
		return $this->name;
	}

	protected function set_name($name){
		$this->name = $name;
	}

	private function return_class_name(){
		return 'Person';
	}

	public function return_string(){
		return 'hello';
	}
}

$tom = new Person;
echo '<pre>';
print_r($tom);
echo '</pre>';
/*
Person Object
(
    [name] => stone
    [sex:protected] => 
    [age:Person:private] => 
)
*/
$tom->name = 'tom';
echo $tom->return_name(); // tom
echo '<br/>';
echo $tom->return_string(); // hello 

class Programmer extends Person
{
	function return_string(){
		return 'world';
	}
}

$stone = new Programmer;
echo '<pre>';
print_r($stone);
echo '</pre>';
/*
Programmer Object
(
    [name] => stone
    [sex:protected] => 
    [age:Person:private] => 
)
*/
var_dump($stone->introduction); 
// Notice: Undefined property: Programmer::$introduction in
// NULL
echo '<br/>';
$stone->introduction = 'I am a programmer';
echo $stone->introduction; // I am a programmer
echo '<br/>';
var_dump($stone->name); // string(5) "stone" 
echo '<br/>';
echo $stone->return_name(); // stone
echo '<br/>';
echo $stone->return_string(); // world
```
- 子类会继承父类所有公有和受保护的方法，子类可以通过重写来覆盖父类的方法。
- 父类必须在子类之前被声明。
- 继承需要使用关键字`extends`。
- 父类的属性也会被子类继承。

#### 构造函数和析构函数
构造函数用于在实例化一个类为对象时做一些初始化的操作，构造函数是类中一个在新建对象时会被自动调用的方法。析构函数在对象所有引用被删除或对象被显示销毁时会被调用，析构函数适合做一些清理和收尾工作。
```php
class Person
{
	function __construct(){
		echo 'this is a construct';
	}

	function __destruct(){
		echo 'this is a destruct';
		echo '<br/>';
	}
}

$tom = new Person; // this is a construct

class Programmer extends Person
{
	function __construct(){
		parent::__construct();
		echo '<br/>';
		echo 'this is a programmer construct';
	}

	function __destruct(){
		parent::__destruct();
		echo 'this is a programmer destruct';
		echo '<br/>';
	}
}
echo '<br/>';
$stone = new Programmer;
/*
this is a construct
this is a programmer construct
*/

class Saler extends Person
{
	
}
echo '<br/>';
$jim = new Saler; // this is a construct

class Animal
{
	public $name;

	function __construct($name){
		$this->name = $name;
	}

	function get_name(){
		return $this->name;
	}

	function __destruct(){
		$this->name = null;
		echo 'this is an Animal destruct';
		echo '<br/>';
	}
}

$nick = new Animal('nick');
echo '<br/>';
echo $nick->get_name(); // nick
echo '<br/>';
/*
this is an Animal destruct
this is a destruct
this is a destruct
this is a programmer destruct
this is a destruct
*/
```
- 构造函数的名称为`__construct`。
- 析构函数的名称为`__destruct`。
- 子类可以继承父类的非`private`构造函数，在子类覆盖了父类的构造函数时如果要调用父类的构造函数可以通过使用`parent::__construct`来进行。
- 构造函数可以有参数，析构函数不可以有参数，构造函数和析构函数都不能有返回值。
- 子类可以继承父类的非`private`析造函数，在子类覆盖了父类的析造函数时如果要调用父类的析造函数可以通过使用`parent::__destruct`来进行。

#### 访问控制
通过访问控制可以指定类的成员（包括属性和方法）的访问范围，可以通过在类成员前面加上修饰符`public`, `protected`或`private`来指定访问控制。
```php
class Person
{
	var $name = 'tom';
	protected $sex = 'male';
	private $age = 30;
	public $introduction = 'I am a person';

	function echo_info(){
		echo $this->name;
		echo '<br/>';
		echo $this->sex;
		echo '<br/>';
		echo $this->age;
		echo '<br/>';
		echo $this->introduction;
	}

	function a_public_function(){
		echo 'this is a public function in Person';
		echo '<br/>';
	}

	protected function a_protected_function(){
		echo 'this is a protected function in Person';
		echo '<br/>';
	}

	private function a_private_function(){
		echo 'this is a private function in Person';
		echo '<br/>';
	}

	public function show_function(){
		$this->a_public_function();
		$this->a_protected_function();
		$this->a_private_function();
	}
}

$tom = new Person();
echo '<pre>';
print_r($tom);
echo '</pre>';
/*
Person Object
(
    [name] => tom
    [sex:protected] => male
    [age:Person:private] => 30
    [introduction] => I am a person
)
*/

$tom->echo_info(); 
/*
tom
male
30
I am a person
 */
echo '<br/>';
echo $tom->name; // tom
echo '<br/>';
// echo $tom->sex; // Fatal error: Uncaught Error: Cannot access protected property Person::$sex in 
echo '<br/>';
// echo $tom->age; // Fatal error: Uncaught Error: Cannot access private property Person::$age in
echo '<br/>';
echo $tom->introduction; // I am a person
echo '<br/>';
$tom->a_public_function(); // this is a public function in Person
// $tom->a_protected_function(); // Fatal error: Uncaught Error: Call to protected method Person::a_protected_function() from context '' in
// $tom->a_private_function(); // Fatal error: Uncaught Error: Call to private method Person::a_private_function() from context '' in
$tom->show_function();
/*
this is a public function in Person
this is a protected function in Person
this is a private function in Person
*/

class Programmer extends Person
{
	public $name = 'stone';
	
	function echo_info(){
		echo $this->name;
		echo '<br/>';
		echo $this->sex;
		echo '<br/>';
		echo $this->age;
		echo '<br/>';
		echo $this->introduction;
		echo '<br/>';
	}

	public function programmer_show_function(){
		$this->a_public_function();
		$this->a_protected_function();
		// $this->a_private_function(); // Fatal error: Uncaught Error: Call to private method Person::a_private_function() from context 'Programmer' in
	}
}

$stone = new Programmer;
echo '<pre>';
print_r($stone);
echo '</pre>';
/*
Programmer Object
(
    [name] => stone
    [sex:protected] => male
    [age:Person:private] => 30
    [introduction] => I am a person
)
*/
echo $stone->name; // stone
echo '<br/>';
// echo $stone->sex; // Fatal error: Uncaught Error: Cannot access protected property Programmer::$sex in
echo '<br/>';
echo $stone->age; // Notice: Undefined property: Programmer::$age in
echo '<br/>';
$stone->echo_info();
/*
stone
male

Notice: Undefined property: Programmer::$age in D:\www\test\test1.php on line 59

I am a person
*/
$stone->a_public_function(); // this is a public function in Person
// $stone->a_protected_function(); // Fatal error: Uncaught Error: Call to protected method Person::a_protected_function() from context '' in 
// $stone->a_private_function(); // Fatal error: Uncaught Error: Call to private method Person::a_private_function() from context '' in
$stone->show_function();
/*
this is a public function in Person
this is a protected function in Person
this is a private function in Person
 */
$stone->programmer_show_function();
/*
this is a public function in Person
this is a protected function in Person
*/

class Saler extends Person
{
	function a_public_function(){
		echo 'this is a public function in Saler';
		echo '<br/>';
	}

	protected function a_protected_function(){
		echo 'this is a protected function in Saler';
		echo '<br/>';
	}

	private function a_private_function(){
		echo 'this is a private fucntion in Saler';
		echo '<br/>';
	}

	public function saler_show_function(){
		$this->a_public_function();
		$this->a_protected_function();
		$this->a_private_function();
	}
}

$jim = new Saler;
$jim->a_public_function(); // this is a public function in Saler
// $jim->a_protected_function(); // Fatal error: Uncaught Error: Call to protected method Saler::a_protected_function() from context '' in
// $jim->a_private_function(); // Fatal error: Uncaught Error: Call to private method Saler::a_private_function() from context '' in
$jim->show_function();
/*
this is a public function in Saler
this is a protected function in Saler
this is a private function in Person
*/
$jim->saler_show_function();
/*
this is a public function in Saler
this is a protected function in Saler
this is a private fucntion in Saler
 */

class Animal
{
	private $name;
	function __construct($name){
		$this->name = $name;
	}

	private function echo_name(){
		echo 'my name is '.$this->name;
		echo '<br/>';
	}

	function access_private(Animal $animal){
		// $animal->name = 'tom';
		$animal->echo_name();
	}
}

$jack = new Animal('jack');
// $jack->echo_name(); // Fatal error: Uncaught Error: Call to private method Animal::echo_name() from context '' in
// echo $jack->name; // Fatal error: Uncaught Error: Cannot access private property Animal::$name in
$jack->access_private(new Animal('lucy')); // my name is lucy
```
- 被`public`修饰的类成员是公有的，可以在任何地方被访问。
- 被`protected`修饰的类成员是受保护的，可以被类本身，子类和父类访问。
- 被`private`修饰的类成员是私有的，只能被类本身访问。
- 没有被访问控制关键字修饰的类成员被认为是公有的，即`public`。
- 子类会继承父类的公有和受保护的类成员，可以重写这些这些类成员。
- 若想访问其它对象的私有或受保护的属性和方法则可以通过将对象作为参数传递给另一个对象的方法来实现。

#### 类的自动加载
通过类的自动加载可以避免冗长的文件加载列表，在`php`中可以使用函数`spl_autoload_register()`来完成类的自动加载。
```php
// Person.php
class Person
{
	public $name;

	function say_something(){
		echo 'I say something';
		echo '<br/>';
	}
}

// Programmer.php
class Programmer extends Person
{
	public $name;

	function coding(){
		echo 'I am coding...';
		echo '<br/>';
	}
}

// Animal.php
class Animal
{
	public $name;
	
	function eat(){
		echo 'I am eating';
	}
}

// index.php
/*require_once('./Person.php');
require_once('./Programmer.php');
require_once('./Animal.php');*/
spl_autoload_register(function($class_name){
	require_once $class_name.'.php';
});

$tom = new Person();
$tom->say_something(); // I say something

$stone = new Programmer();
$stone->say_something(); // I say something
$stone->coding(); // I am coding...

$jack = new Animal;
$jack->eat(); // I am eating
```

#### 范围解析操作符
在`php`中，由两个冒号组成的运算符`::`被称为范围解析操作符，通过`::`可以访问类的静态成员和类常量，还可以通过范围解析操作符来覆盖类的属性和方法。
```php
class Person
{
	// const CONST_VAR; // Parse error: syntax error, unexpected ';', expecting '=' in 
	const CONST_VAR = 'A CONST VARIABLE';

	static function return_const(){
		// return $this->CONST_VAR; // Fatal error: Uncaught Error: Using $this when not in object context in
		return self::CONST_VAR;
	}

	protected function a_function(){
		echo self::return_const();
		echo '<br/>';
		echo 'this is a protected funtion in Person';
		echo '<br/>';
	}
}

echo Person::CONST_VAR; // A CONST VARIABLE
echo '<br/>';
// echo Person::return_const(); // Fatal error: Uncaught Error: Using $this when not in object context in
$tom = new Person;
// echo $tom->return_const(); // Fatal error: Uncaught Error: Using $this when not in object context in
echo Person::return_const(); // A CONST VARIABLE
echo '<br/>';
$class_person = 'Person';
echo $class_person::CONST_VAR; // A CONST VARIABLE
echo '<br/>';
echo $class_person::return_const(); // A CONST VARIABLE
echo '<br/>';

class Programmer extends Person
{
	public static $static_var = 'a static variable';

	public static function echo_const_static(){
		// echo self::CONST_VAR; // A CONST VARIABLE
		echo parent::CONST_VAR;
		echo '<br/>';
		echo self::$static_var;
		echo '<br/>';
	}

	function a_function(){
		parent::a_function();
		echo 'this is a function in Programmer';
		echo '<br/>';
	}
}

$stone = new Programmer;
// echo $stone->static_var;
// Notice: Accessing static property Programmer::$static_var as non static in
// Notice: Undefined property: Programmer::$static_var in
$stone->echo_const_static();
// A CONST VARIABLE
// a static variable
echo Programmer::$static_var;
echo '<br/>'; // a static variable
Programmer::echo_const_static();
/*
A CONST VARIABLE
a static variable
*/
$class_programmer = 'Programmer';
echo $class_programmer::$static_var; // a static variable
echo '<br/>';
$stone->a_function();
/*
A CONST VARIABLE
this is a protected funtion in Person
this is a function in Programmer
*/
```
- 可以通过变量来引用类，但是变量的值不能是`self`, `parent`或`static`。
- 通过`::`运算符可在类内部访问类的本身的常量和静态方法，可以访问父类的类常量和方法。