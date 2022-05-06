## DeepLabv3+优化分割模型在keras当中的实现
---

### 目录
1. [模型效果 model effect](#模型效果)
2. [所需环境 Environment](#所需环境)
3. [注意事项 Attention](#注意事项)
4. [文件下载 Download](#文件下载)
5. [训练步骤 How2train](#训练步骤)
6. [预测步骤 How2predict](#预测步骤)
7. [评估步骤 miou](#评估步骤)

### 所需环境
tensorflow==1.13.2    
keras==2.1.5
（也可在目录下 pip install -r requirements.txt）

### 注意事项
代码中的deeplabv3_mobilenetv2.h5和deeplabv3_xception.h5是基于VOC拓展数据集训练的。训练和预测时注意修改backbone。    

### 文件下载
VOC拓展数据集的百度网盘如下：  
链接: https://pan.baidu.com/s/1BrR7AUM1XJvPWjKMIy2uEw 提取码: vszf   

### 训练步骤
#### 训练voc数据集
1、将提供的voc数据集放入VOCdevkit中（无需运行voc_annotation.py）。  
2、在train.py中设置对应参数，默认参数已经对应voc数据集所需要的参数了，所以只要修改backbone和model_path即可。  
3、运行train.py进行训练。  
 
### 预测步骤
#### 使用预训练权重
1、下载完库后解压，如果想用backbone为mobilenet的进行预测，直接运行predict.py就可以了；如果想要利用backbone为xception的进行预测，在百度网盘下载deeplab_xception.h5，放入model_data，修改deeplab.py的backbone和model_path之后再运行predict.py.   
2、在predict.py里面进行设置可以进行fps测试、整个文件夹的测试和video视频检测。       
  
### 评估步骤
1、设置get_miou.py里面的num_classes为预测的类的数量加1。  
2、设置get_miou.py里面的name_classes为需要去区分的类别。  
3、运行get_miou.py即可获得miou大小。  

