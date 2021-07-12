# Visual Studio 自定义安装程序

1.新建wpf app项目

2.安装installer扩展插件

![image-20210712132121254](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712132121254.png)

![image-20210712131927732](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712131927732.png)

3.Add 安装程序（一次建好，可重复使用，只需再solution中引用<这种方式最简便>,此外，还可在project目录下新建wpf library项目，在项目的本地文件存储位置粘贴文件，在project目录下刷新Refresh，并右击虚线标识的文件，选择include in project)

4.点击solution,右击，选择Add，为该solution创建一个setup项目

![image-20210712132906594](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712132906594.png)

5.在Release模式下，build solution下的所有项目，使其本地release中生成可运行代码

6.右击setup项目

![image-20210712133252226](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712133252226.png)

7.添加主输出 Project Output，选择安装程序的项目作为primary output

![image-20210712133600711](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712133600711.png)

8.在Application Folder中添加(Add File)相关项目的release文件夹中的内容

主程序：

![image-20210712133746129](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712133746129.png)

安装程序：

![image-20210712133819497](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712133819497.png)

放入软件的图标（必须是.ico的格式图片）和卸载程序，以及其他需要在软件安装成功后的安装目录中出现的程序

![image-20210712134046472](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712134046472.png)

msiexec.exe是系统卸载程序，位置C:\Windows\System32中，先拷贝到本地的文件中，再导入进去（因为C:\Windows\System32是系统文件夹）

9.右击setup项目，选择Properties

![image-20210712134426701](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712134426701.png)

点击Prerequisites

![image-20210712134510206](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712134510206.png)

选择自己的系统框架版本

![image-20210712134705253](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712134705253.png)

10.添加快捷方式，为主程序添加快捷方式

![image-20210712134905080](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712134905080.png)

设置setup项目的属性,并复制ProductCode(ProductCode随version变化，在修改version后快捷方式需要重新绑定ProductCode)

![image-20210712135147589](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712135147589.png)

快捷方式需要与ProductCode绑定，Arguments属性改为“/x”+空格+复制的ProductCode

![image-20210712135459557](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712135459557.png)

修改快捷方式的icon

![image-20210712135825709](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712135825709.png)

在这两项下加入快捷方式（方式同上），Desktop是桌面快捷方式,Programs Menu是桌面开始李米娜的程序文件夹

![image-20210712135957509](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712135957509.png)

11.在setup项目中加入Custom Actions，即自定义安装操作，add 主输出文件

![image-20210712140257936](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712140257936.png)

设置属性CustomActionData(用户界面获取到的数据，以及安装程序中需要的参数的对应关系)

此属性是安装文件的路径

![image-20210712140452211](C:\Users\ZQA3WX\AppData\Roaming\Typora\typora-user-images\image-20210712140452211.png)

12.最后build setup项目程序,点击release文件（即最后的安装程序）中setup程序，安装