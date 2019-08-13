##### 问题：**简单说一下hadoop和spark的shuffle过程**

##### 出题人：京东出题专家：阿昀/京东数据中台

##### 参考答案：

Hadoop：map端保存分片数据，通过网络收集到reduce端。

Spark：spark的shuffle实在DAGSchedular划分Stage的时候产生的，TaskSchedular要分发Stage到各个worker的executor。减少shuffle可以提高性能。





