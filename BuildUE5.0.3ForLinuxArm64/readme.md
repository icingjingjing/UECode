UE编译器版本为5.0.3

## Windows下打包LinuxArm64程序

1、**安装交叉编译所需的工具链**。

下载链接为：https://cdn.unrealengine.com/CrossToolchain_Linux/v20_clang-13.0.1-centos7.exe

其他UE版本的工具可从如下链接找到：https://docs.unrealengine.com/5.1/en-US/linux-development-requirements-for-unreal-engine/

2、**UE安装平台支持相关的组件**：

进Epic Launcher->虚幻引擎->库->对应版本的UE->选项

弹出的安装选项中选择：目标平台->Linux。

点应用，完成安装

3、**Plugins中的工程设置**。（如果工程中没有Plugins目录，可以跳过此步骤）

打开Plugins下的插件的uplugin文件，在Modules中添加LinuxArm64的平台支持。示例如下：

```
"Modules": [
		{
			"Name": "TJProduct",
			"Type": "Runtime",
			"LoadingPhase": "Default",
			"WhitelistPlatforms": [
				"Win64",
				"LinuxArm64"
			]
		},
		{
			"Name": "EasyWebsockets",
			"Type": "Runtime",
			"LoadingPhase": "Default",
			"WhitelistPlatforms": [
				"Win64",
				"LinuxArm64"
			]
		}
	]
```

4、**打包程序**

UE打开工程，工具栏选择：Platforms->LinuxArm64->Package Project。(打包之前可以先Cook Content)

注意Log输出，Plugins代码报错的地方，要修改代码，有些插件的代码没有考虑Linux的兼容。

修改后，重新打包，直至成功为止。

5、**压缩打包后的程序**

打开window控制台，使用tar命令压缩成tar.gz格式。方便linux下解压

tar -czf [文件名].tar.gz [文件夹]



## **Linux下部署与运行**：

1、**Linux下解压程序**

tar -xf [文件名].tar.gz

2、**设置程序可执行。鼠标右键属性，把可执行勾上**。

3、**运行程序**

控制台下运行./[文件名].sh即可

