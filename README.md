# PSPNet
PSPNet实现船舶弦号的分割
# 文件下载
psp_resnet50.pth下载地址  
链接: https://pan.baidu.com/s/16rVQK9ibtc0Pj9pOIRLQOw 提取码: ajfk 
# 预测步骤
## 使用预训练权值
（1）本模型可以使用mobilenetv2和resnet50进行训练，如果想用backbone为mobilenet的进行预测，直接运行predict.py就可以了；如果想要利用backbone为resnet50的进行预测，则需要进行一下修改，在文件model_data中有pspnet_resnet50.pth，修改pspnet.py的backbone和model_path之后再运行predict.py，输入。

(2)在pspnet.py文件里面，在如下部分修改model_path和backbone使其对应训练好的文件；model_path和backbone所使用的提取网络相对应，backbone是所使用的主干特征提取网络。
```
_defaults = {
    "model_path"        :   'model_data/pspnet_mobilenetv2.pth',
    "model_image_size"  :   (473, 473, 3),
    "backbone"          :   "mobilenet",
    "downsample_factor" :   16,
    "num_classes"       :   3,
    "cuda"              :   True,
    "blend"             :   True,
}
```

（3）运行predict.py,输入
```
img/1.jpg
```

# 训练步骤
## 1、训练数据集
（1）本次模型使用VOC格式进行训练。

（2）将提供的数据集放入VOCdevkit中，其中将标签文件放在VOCdevkit文件夹下的VOC2007文件夹下的SegmentationClass中。将图片文件放在VOCdevkit文件夹下的VOC2007文件夹下的JPEGImages中。

（3）在训练前利用voc2pspnet.py文件生成对应的txt。

（4）在train.py文件夹下面，选择自己要使用的主干模型和下采样因子。本文提供的主干模型有mobilenet和resnet50。

（5）运行train.py进行训练
