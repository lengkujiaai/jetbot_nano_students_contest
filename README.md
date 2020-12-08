# jetbot_nano_students_contest

# 作者：lengkujiaai@126.com

# 下载模型
模型太大，github上不让放

我训练好的寻路的模型（42.7M）：
https://7869-xiaoxue-3-6-ad8d09-1257746400.tcb.qcloud.la/huangsexian_304zhang_50epoch.pth?sign=872acedad836d3225b8c929f9cf99057&t=1607411127

识别动物的模型（33.3M）：
https://7869-xiaoxue-3-6-ad8d09-1257746400.tcb.qcloud.la/ssd_mobilenet_v2_coco.engine?sign=fe9262c0a086a7d5e6d65605b9122c64&t=1607411160

competition_note.ipynb是比赛的示例代码，小车寻路，遇到第一个需要识别的动物停止10秒，启动后继续寻路，再看到需要识别的第二个动物，小车停止

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
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/download.png)

## 2.6 关闭操作的文件和kernel
执行完一个文件后，记得关闭视窗和kernel。先要点击x号关掉文件，再选铜钱图标，点击SHUT DOWN。要记得关掉所有的kernel，否则后面运行时可能报错。以后没执行完一个文件，都要这样操作。具体见截图：
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/shutdown.png)

# 3、Train Model 训练模型

## 3.1 双击train_model.ipynb打开文件：
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/train_model.png)

## 3.2 引入用到的函数库
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/train_model_import.png)

## 3.3 将压缩文件解压
如果在左侧能看到自己保存寻路图片的文件夹，可以不用执行这一步。如果是用的别人采集的图片，或者即便是自己采集的图片，但只有压缩的文件，就要执行这一步解压
在执行之前要确保要解压缩的文件名在左侧是存在的，如果不存在，则需要修改左侧的文件名或者修改解压命令中压缩包的文件名。如果没有压缩包，需要上传后在修改。
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/unzip.png)

## 3.4 选择训练所用的数据集
如果有多个数据集，训练时把目录改成自己要训练的数据集的文件夹名字
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/train_folder.png)

## 3.5 将数据集分成训练集和验证集

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/split_dataset.png)

## 3.6 设置训练模型的细节

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/train_detail.png)

## 3.7 使用ResNet-18网络

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/resnet_18.png)

## 3.8 将训练过程放到gpu上运行

![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/gpu.png)

## 3.9 修改保存模型的名字及训练回合的次数
原始代码是训练50回合，我用的70.训练太多的回合数可能导致过拟合，也不好。如果训练效果不好，可以试着将NUM_EPOCHS的值改小一点

保存模型的名字也可以改成自己想要的名字
![image](https://github.com/lengkujiaai/jetbot_nano_students_contest/blob/main/image/model_name.png)

训练完成后，你会在左侧看到自己保存的模型的名字。训练模型的时间会随着图片数目的多少而变化。150张图片35个回合大约15分钟。

## 3.10 关闭文件和内核
见上面2.6的图片。每次运行完ipynb文件，都要进行对应的关闭操作，x掉打开的文件，在左侧找到SHUTDOWN，单击所有的SHUTDOWN。

# 4、Live Demo 真实演示
这里就不一一截图解释了，后面我会把做了注释的notebook文档上传到本github下面，方便用户使用



# 另：

1、2020-12-08，现供职于北京中电科卫星导航系统有限公司，本部门为研发中心。

2、公司在淘宝销售nvidia jetson 系列的产品，包括jetson nano，     TX1,     TX2,    AGX XAVIER,        XAVIER NX产品

3、我们属于提供技术支持的，本项目就是北京市海淀区一个比赛的内容，后面会慢慢补充完整。

4、复制链接：   

    2.0fυィ直信息₰gyi7clU3sNj₤回t~bao或點几url链 https://m.tb.cn/h.4WAPC9j?sm=19844c 至浏览er【北京中电科卫星导航公司】
    
后打开淘宝即可

# 技术支持：

![image](https://github.com/lengkujiaai/Face-Recognition/blob/main/readmeImages/%E5%85%AC%E5%8F%B8%E4%BA%A7%E5%93%81.png)



