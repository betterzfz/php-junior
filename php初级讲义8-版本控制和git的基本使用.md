#### 版本控制
- 软件开发通常是以团队进行的，团队成员需要共同为项目编写代码，这个过程中非常容易造成冲突。所以需要为开发团队创建代码仓库，团队成员可以向仓库中提交代码，也可以从仓库中拉取最新的代码，这就为团队的合作构建了一个基础。
- 存储于开发成员本地的代码或是服务器上的代码仓库都是可能会丢失，那么可以通过存放在其它地方的代码仓库进行恢复。
- 版本控制的另一个好处是可以进行版本回退，这样就可以返回到之前的开发版本，这一操作在某些情况下是必要的。
- 常用的版本控制软件包括`git`,`svn`,`cvs`等。
#### git的基本使用
- 以下操作是在已经安装了`git`的计算机上进行的
- 通过命令`git clone 仓库地址`进行代码仓库的克隆

![在指定目录下右击执行`Git Bash Here`.png](http://upload-images.jianshu.io/upload_images/2050891-696d18a93ba68959.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![git-bash-here.png](http://upload-images.jianshu.io/upload_images/2050891-1a8511fb43d3cef0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![git-clone.png](http://upload-images.jianshu.io/upload_images/2050891-0541fa4af3589420.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 切换到克隆出来的文件夹下就可以进行常规的`git`操作了

![cd-dir.png](http://upload-images.jianshu.io/upload_images/2050891-f7c3288fe33b931e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 通过命令`git pull`拉取最新的代码

![git-pull.png](http://upload-images.jianshu.io/upload_images/2050891-1a1aa9e649a39b31.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 通过命令`git status`获取当前工作区的状态

![git-status.png](http://upload-images.jianshu.io/upload_images/2050891-163ee3e99021c9dc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 在工作目录下面创建文件夹`zhuohao`

![mkdir.png](http://upload-images.jianshu.io/upload_images/2050891-449d02962b746b6e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 在目录`zhuohao`下创建文件`test.txt`并向其中写入一些信息

![mk-file.png](http://upload-images.jianshu.io/upload_images/2050891-6bc1ef76384ad7a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 使用`git add`添加文件用于提交

![git-add.png](http://upload-images.jianshu.io/upload_images/2050891-255072d72775d54e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 使用`git commit`将添加文件提交，`-m`用于记录提交注释。

![git-commit.png](http://upload-images.jianshu.io/upload_images/2050891-56320ad07002aff6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 使用`git push`将提交推向服务器

![git-push.png](http://upload-images.jianshu.io/upload_images/2050891-b83dbc8263558403.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 删除本地文件

![delete-file.png](http://upload-images.jianshu.io/upload_images/2050891-5e0bd6381954f66e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 连续执行`git add`, `git commit`, `git push`等命令提交最新的修改，如果当前本地版本不是最新的则需要先执行`git pull`拉取最新的版本，然后才能执行`git push`。

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2050891-6615ec403ba63dd1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)