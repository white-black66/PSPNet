# PSPNet
PSPNet实现船舶弦号的分割
# 预测步骤
## 使用预训练权值
（1）本模型可以使用mobilenetv2和resnet50进行训练，如果想用backbone为mobilenet的进行预测，直接运行predict.py就可以了；如果想要利用backbone为resnet50的进行预测，在文件model_data中有pspnet_resnet50.pth，修改pspnet.py的backbone和model_path之后再运行predict.py，输入。

(2)在pspnet.py文件里面，在如下部分修改model_path和backbone使其对应训练好的文件；model_path和backbone所使用的提取网络相对应，backbone是所使用的主干特征提取网络。
```
_defaults = {
    "model_path"        :   'model_data/pspnet_mobilenetv2.pth',
    "model_image_size"  :   (473, 473, 3),
    "backbone"          :   "mobilenet",
    "downsample_factor" :   16,
    "num_classes"       :   21,
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
（1）将提供的数据集放入VOCdevkit中

（2）在train.py中设置对应参数，默认参数已经对应数据集所需要的参数了，所以只要修改backbone和model_path即可。

（3）运行train.py进行训练
