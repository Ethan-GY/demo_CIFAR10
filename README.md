# demo_CIFAR10
This repository is for practicing using pytorch to deal with CIFAR10 dataset.

# CIFAR10 图像分类项目

## 项目概述

这个项目是使用PyTorch框架对CIFAR10数据集进行图像分类的深度学习实践。项目实现了基于ResNet18架构的卷积神经网络模型，通过数据增强、学习率调整等技术提高模型性能，最终在CIFAR10测试集上进行预测并生成提交文件。

## 环境要求
- PyTorch
- torchvision
- pandas
- d2l库（用于ResNet18模型和辅助函数）


## CIFAR10数据集

CIFAR10是一个包含60,000张32x32彩色图像的数据集，分为10个类别，包括：飞机、汽车、鸟类、猫、鹿、狗、青蛙、马、船和卡车。

本项目支持两种模式：
- 演示模式：使用较小的数据集进行快速训练和测试
- 完整模式：使用完整的CIFAR10数据集进行训练和测试

## 项目结构

```
├── README.md          # 项目说明文档
├── cifar10.ipynb      # Jupyter notebook版本的代码
├── cifar10.py         # Python脚本版本的代码
└── resnet18.py        # ResNet18模型的实现
```

## 数据处理流程

1. **数据下载与组织**：自动下载CIFAR10数据集，并按照训练集、验证集和测试集进行组织
2. **数据增强**：对训练数据进行随机裁剪、水平翻转等增强操作
3. **数据标准化**：对图像数据进行标准化处理

## 模型架构

本项目使用ResNet18模型进行图像分类。ResNet（残差网络）通过引入跳跃连接解决了深度神经网络训练中的梯度消失问题。

ResNet18的主要组件：
- 残差块（Residual Block）：包含两个3x3卷积层和跳跃连接
- 批量归一化（Batch Normalization）：提高训练稳定性
- 自适应平均池化：将特征图转换为固定大小
- 全连接层：输出10个类别的预测概率

## 训练过程

训练参数：
- 批量大小：演示模式为32，完整模式为128
- 训练轮数：20轮
- 学习率：2e-4，每4轮衰减10%
- 权重衰减：5e-4
- 优化器：SGD（动量0.9）
- 损失函数：交叉熵损失

训练策略：
1. 首先在训练集上训练，并在验证集上评估模型性能
2. 然后使用全部训练数据（包括验证集）重新训练模型
3. 最后在测试集上进行预测并生成提交文件
最终测试集检测准确率达到80.5%
<img width="309" alt="image" src="https://github.com/user-attachments/assets/8e0f11f5-2292-495d-b20b-446e7b189f86" />

