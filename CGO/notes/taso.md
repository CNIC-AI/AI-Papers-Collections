# 1. 研究背景

现有的DNN框架都是通过使用人工设计的图替换来优化计算图，这种方法虽然可以提高DNN的计算性能，但是在以下几个方面存在不足：

- Maintainability: 会不断引入新的算子，使得项目难以维护;
- Data Layout: 张量可以任意布局存储，布局对运行时的性能影响较大;
- Correctness: 人工设计的图替换容易出错;

# 2. 研究目的

基于以上的不足之处，本文提出了TASO——第一个自动生成图替换的计算图优化器，并且对生成的等价图替换进行了校验，保证了替换的准确性，与此同时还将图替换和 Layout 进行了联合优化，找到不同替换对应的最佳 Layout，提高运行性能。

# 3. 研究内容

现有DNN框架对计算图的优化流程图：

<div align=center>
    <img src=./../images/taso/existing_dnn_framework.png>
</div>

TASO的计算图的优化流程图：

<div align=center>
    <img src=./../images/taso/taso.png>
</div>

## 3.1 Graph substitution generator

暴力枚举所有可能的计算图，并对图的等价性进行了校验。

## 3.2 Pruning redundant substitutions

采用张量重命名和对具有公共子图的计算图进行冗余消除，得到更为通用的替换，减少冗余图的数量。

## 3.3 Joint Optimizer

使用了MetaFlow中基于cost的回溯搜索来进行优化，遍历替换序列，找到对应替换下的最佳布局。
