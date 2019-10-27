##### **问题**：spark中driver的功能是什么？

##### **出题人**：京东出题专家：阿昀／京东数据中台

##### 参考答案：

用户提交的程序运行起来就是一个driver，他是一个一段特殊的executor进程，这个进程除了一般executor都具有的运行环境外，这个进程里面运行着DAGscheduler Tasksheduler Schedulerbackedn等组件

yarn-cluster模式下：

client将用户程序提交到到spark集群中就与spark集群断开联系了，此时client将不会发挥其他任何作用，仅仅负责提交。在此模式下。AM和driver是同一个东西，但官网上给的是driver运行在AM里，可以理解为AM包括了driver的功能就像Driver运行在AM里一样，此时的AM既能够向AM申请资源并进行分配，又能完成driver划分RDD提交task等工作

yarn-client模式下：

yarn-client模式下，Driver运行在客户端上，先有driver再用AM，此时driver负责RDD生成、task生成和分发，向AM申请资源等 ,AM负责向RM申请资源，其他的都由driver来完成