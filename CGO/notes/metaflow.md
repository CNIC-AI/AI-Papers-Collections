# 1. 研究背景

现有的深度学习框架往往通过使用贪心算法对 DNN 计算图进行转换，往往得不到最优解。

# 2. 研究目的

通过放大搜索空间，增加探索到最优计算图的可能性。

# 3. 研究内容

MetaFlow 概览：

<div align=center>
    <img src=./../images/metaflow/mf_overview.png style=zoom:45%>
</div>

## 3.1 Relaxed graph substitutions

增大了计算图的等价搜索空间，以便探索更多更复杂的计算图，也提升了找到更有计算图的概率。

## 3.2 MetaFlow search algorithm

<div align=center>
    <img src=./../images/metaflow/metaflow.png style=zoom:50%>
</div>

## 3.3 MIN-CUT

将整图进行分割，提高回溯搜索的效率。
