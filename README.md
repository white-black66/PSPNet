# PSPNet
PSPNet实现船舶弦号的分割
# 预测步骤
## 1、使用预训练权值
（1）本模型可以使用mobilenetv2和resnet50进行训练，如果想用backbone为mobilenet的进行预测，直接运行predict.py就可以了；如果想要利用backbone为resnet50的进行预测，在文件model_data中有pspnet_resnet50.pth，修改pspnet.py的backbone和model_path之后再运行predict.py，输入。
