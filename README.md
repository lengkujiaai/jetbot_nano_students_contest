# jetbot_nano_students_contest

# 作者：lengkujiaai@126.com


# 1、连接JupyterLab

先把jetbot小车和准备连接小车的笔记本连到同一个路由器下面,小车联网之后会在小车后面的oled屏幕上看到小车的ip


![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/jetbot_ip.jpg)


把192.168.31.216:8888输入笔记本的浏览器下（我用的浏览器是chrome，个别浏览器可能出问题），回车键，即可看到下面的画面，密码是jetbot


![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/login.png)

## 1.1 查看路径跟随文件结构

路径跟随主要包括搜集资料、训练模型、真实演示三步，分别对应文件data_collection.ipynb、train_model.ipynb、live_demo.ipynb三个文件

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/file_architecture.png)

# 2、Data Collection 资料搜集
## 2.1 点击data_collection.ipynb打开文件，可以看到画面：

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/data_collection_0.png)

我们先看一下比赛地图：
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/contest_map.jpg)

## 2.2 用import引入python的一些模块方便下面的代码使用，包括一些公用的和自己定义的

选中代码行，同时按下Shift 和Enter键即可执行选中的代码，也可以在选中代码时，点击图中红框框出的三角形
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/execute_code.png)


*号的意思是正在执行，*号变成数字后表示已经执行完成，见截图中红框部分。如果执行失败，中括号里面什么也没有，并且会在代码行下面报错

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/star_number.png)

## 2.3 用游戏手柄协助采集图片
我们先看看手柄的样子：
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/game_pad.png)

连上手柄，执行完对应手柄的代码后会看到：
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/game_pad.png2)

## 2.3 起一个自己的名字用来存放搜集的图片

马上就要搜集图片了，可以把文件夹改成自己喜欢的名字用来存储采集的图片

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/image_folder.png)

执行完这块代码，可以看到左侧出现了你命名的文件夹的名字

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/image_folder2.png)

采集图片时，一般的用手挪动小车到一个新的位置，用鼠标拖动x、y的值来调整目标点（也就是绿点）的位置，按游戏手柄上对应的键保存图片。调整x、y的值见截图

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/point_x_y_green.png)

我在代码中设置了手柄的4键执行保存图片，如果你喜欢用其他的键，也可以在代码中改成其他的

## 2.4 搜集图片的技巧

我们的目标是想让小车跟着黄色的线段在路上行驶。所以在用鼠标改变x、y的值移动绿点时，一般的要把绿点放到黄色的线段上。真实场景中，小车是可能偏离黄线的，所以也要拍一些小车偏离黄线时，绿点在黄线上的图片。jetbot官网给的采集图片数目是130多张，但为了更好的效果，我一般都拍摄200多张300张，并且尽可能兼顾到多种情况。如果采集的图片单一或标注绿点不够准确，可能会影响小车寻路的效果。也要尽量避免地图周围有较强光线的干扰。

## 2.5 把搜集到的图片压缩成zip文件

根据日期来命名压缩包

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/zip_image.png)

压缩完可以下载到本地保存，右键单击对应的压缩包，在弹出框点击Download


# 3、Train Model 训练模型

# 4、Live Demo 真实演示
