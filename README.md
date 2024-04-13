# 导入数据集
**1.将以下两行中的代码中的地址修改为本地的保存地址**

trainset = datasets.FashionMNIST(root='E:\\3_硕士_复旦大学\\1-研一\\2-第二学期\\神经网络和深度学习\\作业\\作业1', train=True, download=True)

testset = datasets.FashionMNIST(root='E:\\3_硕士_复旦大学\\1-研一\\2-第二学期\\神经网络和深度学习\\作业\\作业1', train=False, download=True)

# 训练
**找到含有以下三行代码的代码块，调参、运行（记得运行前面的代码以激活定义的代码）。**

model = ThreeLayerNN(input_size=784, hidden_size=225, output_size=10, init_params = None)

- input_size: 输入样本的维度，每张图片28*28，reshape展平后，28*28=784
- hidden_size: 隐藏层大小
- output_size: 十分类输出
- init_params: 模型参数导入选项

sgd = SGD(params = model.params, grads = model.grads, learning_rate = 0.1, momentum = 0.9, decay_lr = 1)

- params: 模型参数
- grads: 模型梯度
- learning_rate: 学习率
- momentum: 动量
- decay_lr: 每轮的学习率的缩放比例
  
train(X_train, y_train, X_test, y_test, model, sgd, batch_size = 50, epoch = 100, l2_reg=0, save_threshold = 0.0)

- X_train: 训练集的X
- y_train: 训练集的标签
- X_test: 测试集的X
- y_test: 测试集的标签
- model: 模型
- sgd: 随机梯度下降
- batch_size: 批量大小
- epoch: 训练轮次
- l2_reg: L2正则化的系数
- save_threshold: 模型参数保存时最低的测试集正确率要求（初始可默认为0，在训练过程中会自动修改这个值变成最大值）

# 测试
**1.导入模型参数，并测试**

在以下这一行中，修改directory为保存模型参数的文件夹：   

directory = r"E:\3_硕士_复旦大学\1-研一\2-第二学期\神经网络和深度学习\作业\作业1"

定义需显性显示的测试样本个数，如已有的num = 50。

**2.点击运行**

运行后会：
- 输出该模型参数的文件名
- 自动化计算该模型参数对应的模型，在测试集上的正确率
- 输出前num个测试集数据的运行结果
  - 正确个数、正确比例
  - pd.dataframe 
