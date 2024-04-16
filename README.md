# 导入数据集
**1.将以下两行中的代码中的地址修改为本地的保存地址**

![image](https://github.com/He1senbergg/homework1/assets/148076707/c4f3301f-d268-41b6-b4d0-88c8a8d8f6d1)

trainset = datasets.FashionMNIST(root="/home/ly/miniconda3/envs/data", train=True, download=True)

testset = datasets.FashionMNIST(root="/home/ly/miniconda3/envs/data", train=False, download=True)

# 训练
**找到含有以下三行代码的代码块，调参、运行（记得运行前面的代码以激活定义的代码）。**

![image](https://github.com/He1senbergg/homework1/assets/148076707/b92477d6-b52e-49b7-b3db-e2699b7ab9b3)

model = ThreeLayerNN(input_size=784, hidden_size1=361, hidden_size2=100, output_size=10, init_params = None)

- input_size: 输入样本的维度，每张图片28*28，reshape展平后，28*28=784
- hidden_size1: 隐藏层大小1
- hidden_size2: 隐藏层大小2
- output_size: 十分类输出
- init_params: 模型参数导入选项(None or Saved_params)

sgd = SGD(params = model.params, grads = model.grads, learning_rate = 0.1, momentum = 0, decay_lr = 1)

- params: 模型参数
- grads: 模型梯度
- learning_rate: 学习率
- momentum: 动量(self.velocity[key] = self.momentum * self.velocity[key] - self.lr * dW)
- decay_lr: 每轮的学习率的缩放比例(如lr_new = lr_old * decay_lr)
  
train(X_train, y_train, X_test, y_test, model, sgd, batch_size = 50, epoch = 100, l2_reg=0.001, save_threshold = 0.85)

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

![image](https://github.com/He1senbergg/homework1/assets/148076707/6e6a651d-a733-4c13-9b64-d8dd3f68c694)

directory = "/home/ly"

定义需显性显示的测试样本个数，如已有的num = 50(至多显性前60个结果)。

**2.点击运行**

运行后会：
- 输出该模型参数的文件名
- 自动化计算该模型参数对应的模型，在测试集上的正确率
- 输出前num个测试集数据的运行结果
  - 正确个数、正确比例
  - pd.dataframe 
