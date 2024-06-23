# AutoCF-code
# 论文 Automated Self-Supervised Learning for Recommendation
此存储库包含以下论文中提出的<a href='https://github.com/akaxlh' target='_blank'>@akaxlh</a> 对 AutoCF 模型的 pyTorch 实现：
><a href='https://akaxlh.github.io/' target='_blank'>Lianghao Xia</a>, <a href='https://sites.google.com/view/chaoh' target='_blank'>Chao Huang</a>, Chunzhen Huang, Kangyi Lin, Tao Yu and Ben Kao. <i>Automated Self-Supervised Learning for Recommendation</i>. <a href='https://arxiv.org/abs/2303.07797'>Paper in arXiv</a>. In WWW'23, Austin, US, April 30 - May 4, 2023.

## 介绍
大多数对比方法的成功在很大程度上依赖于手动生成有效的对比视图来进行基于启发式的数据增强。这不能推广到不同的数据集和下游推荐任务，这很难适应数据增强，并且对噪声扰动具有鲁棒性。为了能够训练模型实现自动化的数据增强，AutoCF 设计了一种自动图增强方法，并且实现了一个掩码自动编码器。

<img src='figs/framework.png'>

## 引用
```
@inproceedings{autocf2023,
  author    = {Xia, Lianghao and
               Huang, Chao and
               Huang, Chunzhen and
               Lin, Kangyi and
               Yu, Tao and
               Kao, Ben},
  title     = {Automated Self-Supervised Learning for Recommendation},
  booktitle = {The Web Conference (WWW)},
  year      = {2023},
}
```

## 实验环境
The implementation for AutoCF is under the following development environment:
* python=3.10.4
* torch=1.11.0
* numpy=1.22.3
* scipy=1.7.3

## 数据集
数据集划分：训练集 : 验证集 : 测试集=70% : 5% : 25%
| Dataset | \# Users | \# Items | \# Interactions | Interaction Density |
|:-------:|:--------:|:--------:|:---------------:|:-------:|
|Yelp   |$42,712$|$26,822$|$182,357$|$1.6\times 10^{-4}$|
|Gowalla|$25,557$|$19,747$|$294,983$|$5.9\times 10^{-4}$|
|Amazon |$76,469$|$83,761$|$966,680$|$1.5\times 10^{-4}$|

## 代码使用方法
请先解压缩数据集。此外，您还需要创建 `History/` 和 `Models/` 目录。将工作目录切换到 `methods/AutoCF/` 。使用我们预先训练的在三个数据集上训练 AutoCF 的命令行如下所示。命令中未指定的超参数设置为默认值。

* Yelp
```
python Main.py --data yelp --reg 1e-4 --seed 500
```
* Gowalla
```
python Main.py --data gowalla --reg 1e-6
```
* Amazon
```
python Main.py --data amazon --reg 1e-5 --seed 500
```

### 重要论点
* `reg`: 权重衰减正则化的权重。我们从集合中调整这个超参数。 `{1e-3, 1e-4, 1e-5, 1e-6, 1e-7, 1e-8}`.
* `seedNum`: 此超参数表示子图掩码中的种子数。建议的值为 `{200, 500}`.
