#### php脚本的特点
* `php`脚本是以文件形式存在的，文件的后缀通常为`.php`，这主要取决服务器的配置。
* `php`脚本以标记`<?php`开始，以标记`?>`结束，标记间的代码会被服务器解释执行。
* `php`支持`c`(/**/), `c++`(//)和`perl`(#)风格的注释，注释用于对代码进行简短说明以方便团队合作和后续的维护开发，注释的内容在脚本执行过程中会被忽略。

#### 实例
* 在`web`服务根目录下新建文件`test-3.php`。
* `test-3.php`中写入如下内容：
```php
<?php 
    /**
     * 第一个php脚本
     * @author stone
     */

    # 输出'hello, world!'
    echo 'hello, world!'; // 输出'hello, world!'
?>
```
* 在浏览器中输入[http://localhost/test-3.php](http://localhost/test-3.php)进行访问，如下：

![test-3-1.png](http://upload-images.jianshu.io/upload_images/2050891-78e27e4341886954.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 说明
* `echo`是`php`的一个语言结构，用于信息的打印输出。
* `'hello, world!'`是一个字符串，可以用于各种处理和运算，也可以被直接打印输出。
* `echo 'hello, world!';`是一条`php`语句，`php`语句以`;`结尾，脚本结束标记`?>`可以隐含得表示一个`;`。
* 只有在开始标记`<?php`和结束标记`?>`之间的代码才会被`php`解释器解析，以便于`php`可以嵌入`html`等其它文档，如：
```php
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="utf-8" />
        <title>test</title>
    </head>
    <body>
        <h1><?php echo 'this is a title'; ?></h1>
    </body>
</html>
```
* 如果开启了`short_open_tag`，在嵌入`html`时可以使用短标记`<?`和`?>`等，但是`php`开发组可能会在未来的版本中移除该特性，所以并不推荐这么使用。如：
```php
<!DOCTYPE html>
<html lang="zh-CN">
    <head>
        <meta charset="utf-8" />
        <title>test</title>
    </head>
    <body>
        <h1><?= 'this is a title' ?></h1>
    </body>
</html>
```
* 如果脚本文件是纯的`php`代码，则文件末尾的结束标记`?>`可以被删除，这么做是值得被鼓励的，这样可以避免由于结束标记`?>`之后意外引入换行符和空格而造成的多余输出。脚本`test-3.php`的内容可以改为：
```php
<?php 
    echo 'hello, world!';
```