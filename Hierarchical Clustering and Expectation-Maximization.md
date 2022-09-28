# Hierarchical Clustering and Expectation-Maximization
## Clustering
### Clustering set-up
![Pasted image 20220526145609](Hierarchical Clustering and Expectation-Maximization.assets/Pasted image 20220526145609.png)
### Similarity Measures
![Pasted image 20220526145652](Hierarchical Clustering and Expectation-Maximization.assets/Pasted image 20220526145652-16643504499315.png)

### Hierarchical clustering
- Create a hierarchical decomposition of the set of objects using some criterion
-使用某种标准对对象集进行分层分解
![Pasted image 20220526145829](Hierarchical Clustering and Expectation-Maximization.assets/Pasted image 20220526145829.png)
### Dendrogram: A visual representation of output
![Pasted image 20220526145911](Hierarchical Clustering and Expectation-Maximization.assets/Pasted image 20220526145911-166435047685311.png)
### Measuring distance between clusters

![Pasted image 20220526150028](Hierarchical Clustering and Expectation-Maximization.assets/Pasted image 20220526150028.png)
### Strengths, weaknesses, caveats
#### Strengths
- provides deterministic results
- no need to specify number of clusters beforehand
- can create clusters of arbitrary shapes
#### Weakness
- does not scale up for large datasets, time complexity at least O(n2)
#### Caveats
- Different decisions about group similarities can lead to vastly different dendrograms.
- The algorithm imposes a hierarchical structure on the data, even data for which such structure is not appropriate.


## K-means
- Centroid-based: describe each cluster by its mean
- Goal: assign data to K.
- Algorithm objective: minimize the within-cluster variances of all clusters.
-算法目标：最小化所有群组的群组内方差。
- A non-deterministic method
- Finds a local optimal result (multiple restarts are often necessary)
-找到一个局部最优结果（往往需要多次重启）。
![Pasted image 20220526150819](Hierarchical Clustering and Expectation-Maximization.assets/Pasted image 20220526150819.png)


# 聚类
## Agglomerative Clutsering
Agglomerative Clutsering 是一种**自底而上**的层次聚类方法，它能够根据指定的相似度或距离定义计算出类之间的距离。（Hierarchical clustering两种方式的其中一种，另一种是divisive,自顶而下）
Dendrogram：依次将符合条件的类相连，最后得到使算法与数据均形象化的树状结构图。Dendrogram专门用来描述经层次聚类算法得到的结果。

  Agglomerative Clustering Algorithm
1.将每一个元素单独定为一类
2.重复：每一轮都合并指定距离(对指定距离的理解很重要)最小的类
3.直到所有的元素都归为同一类

Agglomerative Clustering的三种不同方法
依据对相似度（距离）的不同定义，将Agglomerative Clustering的聚类方法分为三种：Single-linkage,Complete-linkage和Group average.
Single-linkage:要比较的距离为元素对之间的最小距离
Complete-linkage:要比较的距离为元素对之间的最大距离
Group average：要比较的距离为类之间的平均距离（平均距离的定义与计算：假设有A，B两个类，A中有n个元素，B中有m个元素。在A与B中各取一个元素，可得到他们之间的距离。将nm个这样的距离相加，得到距离和。最后距离和除以nm得到A，B两个类的平均距离。）

聚合层次聚类的时间复杂度是O(n3m),其中m样本的维数，n是样本个数。

## K-means
### 概念
聚类是一个将数据集中在某些方面相似的数据成员进行分类组织的过程，聚类就是一种发现这种内在结构的技术，聚类技术经常被称为无监督学习。
k均值聚类是最著名的划分聚类算法，由于简洁和效率使得他成为所有聚类算法中最广泛使用的。给定一个数据点集合和需要的聚类数目k，k由用户指定，k均值算法根据某个距离函数反复把数据分入k个聚类中。

假设对基本的二维平面上的点进行K均值聚类，其实现基本步骤是：

1.事先选定好K个聚类中心（假设要分为K类）。
2.算出每一个点到这K个聚类中心的距离，然后把该点分配给距离它最近的一个聚类中心。
3.更新聚类中心。算出每一个类别里面所有点的平均值，作为新的聚类中心。
4.给定迭代此次数，不断重复步骤2,3，达到该迭代次数后自动停止