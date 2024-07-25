# openMV_vision_model
## 一、准备材料：

1.OpenMV4 Plus（低版本的openmv可能算力不够不支持）
2.一根micro usb的数据线
3.电脑、网络

## 二、软件下载

在openMV官网下载openmv IDEhttps://book.openmv.cc/

## 三、使用openMV IDE采集目标数据

### 3.1打开openmv IDE在工具栏中选择新建数据集

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-1024x551.png)

### 3.2在新建数据集内新建两个文件夹用于存放两个不同种类的电路板数据集

![img](http://47.120.12.121/wp-content/uploads/2024/07/屏幕截图-2024-07-25-110318.png)

### 3.3连接openMV进行数据采集

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-2-1024x533.png)

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-3-1024x546.png)对两个电路板均进行数据收集

## 四、导出数据并建立模型

可以使用云端的[edge impulse](https://www.edgeimpulse.com/)网站来进行模型的训练及自动生成。只需要将我们刚刚得到的数据集上传即可获得openmv可使用的训练模型，并进行目标识别。

### 4.1使用edge impulse新建一个工程

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-4-1024x528.png)

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-5-1024x507.png)

### 4.2导入数据

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-6-1024x498.png)

进入工程后点击keys

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-7-1024x217.png)

复制API KEY并在openMV上进行数据上传，如果因为key太长无法复制，可以按F12进入调试窗口复制

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-8-1024x392.png)

复制后在openMV中选择用API上传数据集

![啥](http://47.120.12.121/wp-content/uploads/2024/07/image-9-1024x297.png)

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-10.png)填入秘钥

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-11.png)选择训练与测试的数据比

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-13.png)等待上传即可

### 4.3数据处理

点击左边Impulse design进行数据处理和模型生成设置

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-14-1024x462.png)

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-15-1024x460.png)数据处理照我的设置即可

图片处理选择RGB，选择后点击Save Parameters

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-16-1024x473.png)

点击后进入该界面，直接点击Generate features进行数据处理即可，之后等待数据处理结果

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-17-1024x365.png)

数据处理后可以在右边看到两个不同数据的分散程度，如果两种数据混在一起，则说明数据采集过于混杂，模型处理能力会下降

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-18-1024x486.png)

## 4.4模型生成和导出

点击左侧Transfer learning进入模型生成设置，大家按照需设置，设置完成后点击Start training

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-19-1024x464.png)

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-20-1024x242.png)模型生成ing

输出此信息则说明模型生成已经完成，测试集成功率是100%

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-21.png)

点击Versioning输出模型

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-23-1024x457.png)

点击后输出第一版模型

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-24-1024x450.png)

点击Deployment选择openMV模板输出模型

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-25-1024x444.png)

此时模型已经自动下载好了

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-27-1024x345.png)

## 五、导入模型并完成识别任务

### 5.1连接开发板并导入模型

将openMV开发板连接到电脑并将下载好的压缩包的内容复制到开发板中

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-28-1024x521.png)

### 5.2连接IDE并运行

使用IDE打开压缩包中的py文件并连接openMV运行模型进行检测

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-29-1024x515.png)绿色PCB识别

![img](http://47.120.12.121/wp-content/uploads/2024/07/image-30-1024x501.png)蓝色PCB识别

## 六、结语

本实验验证了openMV利用神经网络训练模型各种不同任务下的识别与分类，通过训练模型可以使openMV进行更广泛的视觉识别和分类，大大提高了openMV的可用性与在实际工程中的应用性，本模型将开源在github上大家也可以自行尝试，并运用神经网络进行模型训练完成其他项目。
