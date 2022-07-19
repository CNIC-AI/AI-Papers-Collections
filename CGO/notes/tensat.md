# 1. 研究背景

深度学习框架中最主要的优化之一是图重写(graph rewriting)。深度学习框架使用启发式算法去决定是否进行重写以及重写的顺序。现有的计算图优化方法都是按照一定的顺序进行图重写的替换，例如使用手动设置重写规则的顺序或者依赖启发式算法来决定重写的顺序，这种方式往往不能得到最优的计算图。

# 2. 研究目的

解决重写顺序依赖的问题。借助Equality Saturation技术，通过一次性应用所有有效的重写来缓解Phase-ordering问题，进而帮助找到更优的计算图。

# 3. 研究内容

tensat 整体流程：

<div align=center>
    <img src=./../images/tensat/tensatflow.png style=zoom:50%>
</div>

## 3.1 Exploration phase

使用重写规则生成 e-graph，该 e-graph 中包含了所有重写的可能且有效的顺序。

## 3.2 Extraction Phase

根据 cost function 从 e-graph 中选出最优的顺序。因为e-graph生成的过程中引入了环，所以这个部分还做了环过滤的操作。
