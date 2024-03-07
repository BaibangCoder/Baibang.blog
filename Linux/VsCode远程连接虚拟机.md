# VS Code使用ssh远程连接Ubuntu

需要事先打开虚拟机

然后才能使用VsCode连接

在虚拟机中使用这条命令，安装ssh服务

![576671271a1f72af8c14766a0dc1bf0](assets/576671271a1f72af8c14766a0dc1bf0.png)

在Linux中使用`ifconfig`命令查看虚拟机的IP地址：

![image-20240307174136134](assets/image-20240307174136134.png)

然后打开VsCode ， 安装插件

![image-20240307171948505](assets/image-20240307171948505.png)

安装后打开，进行添加：

![image-20240307172211101](assets/image-20240307172211101.png)

打开设置后，添加设置

![image-20240307172250531](assets/image-20240307172250531.png)

`Host` 随便写，就是个名字

`HostName` 是虚拟机的IP地址，就是前面用ifconfig获取的地址

`User`就是虚拟机的用户名，就是在虚拟机终端中@前面的那个

![image-20240307172600347](assets/image-20240307172600347.png)

`IdentityFile `可以不用填写

不填的话每次使用都需要输入密码，要填的话在Windows中打开终端，使用`ssh-keygen -t rsa` 获取一个密钥，然后把地址填在后面。

输入命令后，一直点回车，直到出现下图的东西。

![image-20240307172837359](assets/image-20240307172837359.png)



然后点击，下图位置，启动虚拟机，进去后悬着Linux，然后根据提示输入虚拟机的用户密码

![image-20240307173121680](assets/image-20240307173121680.png)

然后就可以正常使用了，新建立终端也是直接用的Linux的终端。