# Linux学习笔记（一）

标签： Linux 笔记

---

## 档案与权限

档案类型与权限（共十个字符）：

“-rwxrwx---”

- 第一个字符代表这个档案是“目录、档案、或连接档等等”：
    * 当为【d】则是目录
    * 当为【-】则是档案
    * 当为【l】则是连接档（link file）
    * 当为【b】则是装置中可供储存的周边设备（可随机存取装置）
    * 当为【c】则是装置中的序列埠设备，如键盘鼠标
    
- 接下来的字符中，三个为一组，且均为“rwx”中的一个。其中：【r】代表可读（read），【w】代表可写（write），【x】代表可执行（execute）。
    * 第一组为【档案拥有者权限】
    * 第二组为【群组账号权限】
    * 第三组为【其他人（others）的权限】





## Linux创建用户

### 一、创建用户

Linux中使用命令：`useradd`来创建用户，`passwd`来更改用户密码，方法：

```
useradd yonghuming  #创建一个名为“yonghuming”的用户
passwd yonghuming  #更改名为“yonghuming”用户的密码
```

创建用户后，可以在`/etc/passwd`中查看用户信息，在`/ccetc/shadow`中查看密码相关参数（但是密码是加密状态也就是偷看不了密码），在`/etc/group`中查看用户组：

```
cat /etc/passwd #查看用户信息
cat /etc/shadow #查看密码信息
cat /etc/group #查看用户组
```

### 二、添加sudo权限
一般情况下我们使用新用户只是为了减少root用户下的失误操作，毕竟root权限太大，一不小心就失足恨千古。但是很多时候用一般用户会导致权限不够，所以我们将新用户赋予sudo权限，在用到需要root用户权限才能执行的命令时，在前面添加sudo暂时获取root权限，就可以解决问题了。

首先，用`visudo`命令打开`/etc/sudoers`文件：

```
visudo
```

打开文件后，按键盘s进入编辑状态，然后找到：

    ##Allow root to run any commands anywhere
    root    ALL=(ALL)    ALL
    
在后面添加一行：

    yonghuming    ALL=(ALL)    ALL
    
然后按键盘Esc退出，输入`:wq`保存退出即可。

### 三、切换用户

`$`：普通用户提示符

`#`：root用户提示符


方式一：

```
su yonghuming
```

方式二：

```
su - yonghuming
```

两种方式有什么区别呢？
第一种切换只是把身份切换了，而shell环境却没有变化，而第二种是连shell带身份都切换掉了，换的比较彻底。

同样的，从普通用户切换到root用户或者其他用户也是`su`命令，加不加“-”和前面的区别一样。

此外，从root用户到普通用户还可以直接输入`exit`，这样也可以直接换回普通用户，且连shell环境一起变化。



