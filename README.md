# tensorflow-gpu-2.0趟坑实录

基于https://tensorflow.google.cn tutorials

# 1.1tensorflow-gpu-2.0 cudnn版本不一致

time:2019.9.18

卷积神经网络运行时，提示cudnn7.4.1,tensorflow为7.6编译，报错。

解决办法为升级cudnn版本或者降低tensorflow版本，cuda10.0版本cudnn安装方法：

1）直接拷贝cudnn下载解压后的文件至\CUDA\v10.0文件夹，实测无效。

2）将cuDNN的三个文件（cudnn64_7.dll ，cudnn.h ，cudnn.lib ）复制粘贴到CUDA相同的目录下。

.\cudnn-10.0-windows10-x64-v7.6.2.24\cuda\bin

.\cudnn-10.0-windows10-x64-v7.6.2.24\cuda\include

.\cudnn-10.0-windows10-x64-v7.6.2.24\cuda\lib\x64

到cuda对应目录中：

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\include

C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\lib\x64

# 1.2结构化数据特征列中的组合列报错


time:2019.9.19

暂未搞定

# 1.3 StandardScaler处理pandas.Dataframe数据

time:2019.9.19

StandardScaler处理pandas.Dataframe数据返回的是ndarray，model.fit不能直接处理，需要重新转换为pandas.Dataframe。

# 1.4 PIL Error

time:2019.9.20

Could not import PIL.Image. The use of `load_img` requires PIL

tf.keras.preprocessing.image.ImageDataGenerator中from PIL import Image as pil_image

引入PIL.Image时应保持一致，否则报错


# 1.5 ProfilerNotRunningError: Cannot stop profiling. No profiler is running.

time:2019.11.15

https://blog.csdn.net/weixin_41010198/article/details/102815483

logdir = './cnn_selu_callbacks'--->logdir = os.path.join("cnn_selu_callbacks")

# 1.6 ValueError: Duplicate plugins for name projector


time:2019.11.15

使用tensorboard时报错，并提示采用了不同路径的tensorboard

https://blog.csdn.net/Avada_533/article/details/102223823

在提示的site-packages文件夹下, 删掉tensorboard--2.0.0dist-info
