#### 环境概述
* wamp: windows+apache+mysql+php
* wimp: windows+iis+mysql+php
* lamp: linux+apache+mysql+php
* mamp: mac os x+apache+mysql+php
* nginx也是一个可以用于php的web服务器。

#### 安装配置过程
* apache的安装和配置
1.直接使用`apache`编译好的二进制包，64位，也可以采用可执行安装程序去安装，在linux下可采用编译安装。
2.把解压好的二进制包放在指定的环境文件夹，如图：

![apache位置.png](http://upload-images.jianshu.io/upload_images/2050891-8ff3ac014ca794af.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.在没有安装`apache`服务的情况下，服务不可用，需要先装。apache的服务可以在计算机管理里面管理，如图：

![没有安装apache.png](http://upload-images.jianshu.io/upload_images/2050891-578dab5702a6da16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4.切换到`apache`可执行命令所在目录，如图：

![切换目录.png](http://upload-images.jianshu.io/upload_images/2050891-7f1cd0709c45b095.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5.配置`apache`配置文件`./conf/httpd.conf`，修改`SRVROOT`的值为本机具体的值，也即`apache`所在的目录。
6.安装`apache`服务，执行命令`httpd -k install`，如图：

![安装apache服务.png](http://upload-images.jianshu.io/upload_images/2050891-d8221c3a61b4669c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

7.`apache`服务安装成功后并不能被正确访问，这是因为服务没有启动，需要启动服务。`apache`服务安装完成后可以在计算机管理里找到，并可以进行管理，如图：

![apache启动.png](http://upload-images.jianshu.io/upload_images/2050891-e729eed2f7f99bb1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![apache管理.png](http://upload-images.jianshu.io/upload_images/2050891-89458fa118ff00c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

8.apache可以通过命令`httpd -k start`启动服务，`httpd -k restart`重启服务，`httpd -k stop`和`httpd -k shutdown`停止服务。

![通过命令进行apache的管理.png](http://upload-images.jianshu.io/upload_images/2050891-16bc1a93647742c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

9.如果需要在任意路径下执行`httpd`命令，可以通过配置环境变量来实现，否则在非`httpd.exe`目录下找不到`httpd`命令，如图：


![找不到httpd命令.png](http://upload-images.jianshu.io/upload_images/2050891-d8455b7b84fcf1c1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![输出当前环境变量.png](http://upload-images.jianshu.io/upload_images/2050891-e0008328088b4ad8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![配置环境变量.png](http://upload-images.jianshu.io/upload_images/2050891-091b4e597593db48.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

重新打开`cmd`窗口，可以获取最新环境变量配置，针对`httpd.exe`所在目录的环境变量配置生效后，就可以在任意路径下执行`httpd`命令了，如图：

![任意目录下均可执行httpd命令.png](http://upload-images.jianshu.io/upload_images/2050891-9b0b1a3b400de67d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* php下载和配置
1.直接下载编译好的`php`二进制包，放到环境文件夹下，如图：

![php位置.png](http://upload-images.jianshu.io/upload_images/2050891-40a12a7b43ac8a02.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.配置`apache`支持`php`脚本的访问，在`apache`配置文件`./conf/httpd.conf`中添加如下配置：
```
# 载入php模块，请将路径替换为您本机具体的值。
LoadModule php5_module "D:\stone\wamp\php5.6\php5apache2_4.dll"
# 添加apache对php脚本类型的识别
AddType application/x-httpd-php .php .html .htm
# 添加php配置文件php.ini的所在目录的指定，请将路径替换为您本机具体的值。
PHPIniDir "D:\stone\wamp\php5.6"
```
* mysql的安装与配置
1.使用的是可执行安装程序，如图：

![mysql可执行安装程序.png](http://upload-images.jianshu.io/upload_images/2050891-ff58fc83b29d5343.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.双击进行安装，如图：

![初始化界面.png](http://upload-images.jianshu.io/upload_images/2050891-55661a892b7c003b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![自定义安装.png](http://upload-images.jianshu.io/upload_images/2050891-a8994e7be7cbb6ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![选择安装的功能.png](http://upload-images.jianshu.io/upload_images/2050891-130c8d3b2cefef64.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![开始安装.png](http://upload-images.jianshu.io/upload_images/2050891-bbf0f063da774f89.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![开始配置.png](http://upload-images.jianshu.io/upload_images/2050891-55fc81f4ed373d36.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![网络配置.png](http://upload-images.jianshu.io/upload_images/2050891-4da73573c6cf67b4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![账户配置.png](http://upload-images.jianshu.io/upload_images/2050891-580326eda177cba3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![windows服务.png](http://upload-images.jianshu.io/upload_images/2050891-46b85238353cb1e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![高级配置.png](http://upload-images.jianshu.io/upload_images/2050891-75f042301f432ce7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![执行配置.png](http://upload-images.jianshu.io/upload_images/2050891-1285a837d5eb3007.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![配置完成.png](http://upload-images.jianshu.io/upload_images/2050891-0d912629bc6c412f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![安装完成.png](http://upload-images.jianshu.io/upload_images/2050891-a6987e655cd4187e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.在计算机管理中可以进行`mysql`的管理，如图：

![管理mysql.png](http://upload-images.jianshu.io/upload_images/2050891-daed775e5d12e10c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4.可以通过`cmd`在`mysql`的命令目录下执行mysql的访问，如图：

![进入mysql.png](http://upload-images.jianshu.io/upload_images/2050891-384d7040b94fb98c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5.如果要在任意路径下访问`mysql`需要配置环境变量，如图：

![没有mysql的环境变量.png](http://upload-images.jianshu.io/upload_images/2050891-cfe02b20d61a8d0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![配置mysql的环境变量.png](http://upload-images.jianshu.io/upload_images/2050891-db65baeb0ebf70d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

重新打开`cmd`，即可在任意路径下执行`mysql`命令，如图：

![任意路径访问mysql.png](http://upload-images.jianshu.io/upload_images/2050891-9cff3f5eac605baa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6.通过`php`访问`mysql`，使用如下脚本：
```php
$mysqli = new mysqli('localhost', 'root', 'root');
if ($mysqli->connect_errno) {
        die('connect error('.$mysqli->connect_errno.')'.$mysqli->connect_error);
}
echo 'mysql连接成功！';
$mysqli->close();
```
有可能会报错，如图：

![mysqli的php扩展没有正确加载.png](http://upload-images.jianshu.io/upload_images/2050891-3becebf380c4b8c1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


这个时候需要通过`<?php phpinfo; ?>`检查`php`是否支持`mysqli`，如果不支持，需要开启`mysqli`扩展(通过修改`php.ini`,去除`;extension=php_mysqli.dll`前面的`;`来进行)，并且要能找到这个扩展。在没有配置的情况下，会到`C:\php\ext`下找扩展，如图：

![默认扩展路径.png](http://upload-images.jianshu.io/upload_images/2050891-74a317a861941685.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

可以通过在`php.ini`中配置`extension_dir`来指定`php扩展的路径`。
当在`phpinfo()`中能够看到`mysqli扩展`的信息时，说明这个时候可以使用`mysqli扩展`给我们提供的函数了，如图：

![mysqli扩展.png](http://upload-images.jianshu.io/upload_images/2050891-d639dba3b4ae0af0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


当`php`连接`mysql`的脚本能够正常运行时，说明`php`的安装环境已经完成安装和配置了，如图：

![php成功连接mysql.png](http://upload-images.jianshu.io/upload_images/2050891-59d8847c0c970a61.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


os x 下的环境配置可以参考[Mac OS X El Capitan 配置PHP环境](http://www.jianshu.com/p/94933ae68133)。