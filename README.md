# 结合测地距离场与曲线平滑的遥感图像道路中心线快速提取
### 摘要 
从高分辨遥感图像中快速提取道路信息在地图绘制、城市规划和更新GIS数据库等方面至关重要，半自动道路提取作为道路测绘内业的主要方式，是一项劳动密集型工作。为了降低人工介入代价，提高工作效率，本文提出了一种基于测地距离场的道路中心线快速提取算法。首先利用最佳圆形模板算法，自动估计道路宽度的同时将人工种子调整到道路中心；为了定位道路中心线，提出基于道路显著图的柔性道路中心核密度估计算法，克服了传统道路中心核密度估计中道路分割阈值预设困难的问题；最重要的，本文提出快速生成测地距离场算法，可快速跟踪种子之间的测地线，大大提高了道路中心线提取的效率；最后对测地线坐标进行均值滤波平滑，获得了光滑的道路中心线。大量的实验和对比数据表明，本文算法能够在保证精度的前提下快速提取道路中心线，大幅降低人工介入代价，提高道路提取的工作效率；值得强调的是，本文算法在图像分辨率固定的前提下，提取任意长度道路中心线的耗时近乎相同，且无需设置超参数，具有很好的人机交互体验。

### Dataset
我们使用 [Google Earth](http://www.escience.cn/people/guangliangcheng/Datasets.html) 来评估本文算法的效率.


### 实验结果

#### 程序演示
以下视频是两个实验案例的执行过程.  
<a href='videos/demo1.mp4?raw=true'/>视频 1. 在image1上的道路提取过程 (612KB).(点击查看)</a>
<br />
<br />
<a href='videos/demo2.mp4?raw=true'/>视频 2. 在image2上的道路提取过程 (464KB).(点击查看)</a>

从提取过程的演示可以看出，本文算法无需设置任何超参数.

#### 提取结果
以下展示几个比较复杂的情况，
<p>
    <img src='images/image11.png?raw=true' />
</p>
<p>
    <img src='images/image13.png?raw=true' />
</p>
<p>
    <img src='images/image20.png?raw=true' />
</p>
<p>
    <img src='images/image34.png?raw=true' />
</p>
<p>
    <img src='images/image155.jpg?raw=true' />
</p>


<h3> 算法执行时间 </h3>

实验操作环境为4核1.8GHz i7处理器，16G内存笔记本，实现语言为Python3.7，三种算法的迭代部分由numba加速
我们提取三条不同长度的道路中心线。如下图所示，三个路段分别为AB、AC和AD，道路长度分别约为480米、990米和1310米。
<p>
    <img src='images/Fig8-c.png?raw=true' />
</p>  
为了使数据更加可信，我们为每个片段提取三次。时间消耗如下所示

|segment|1st|2nd|3th|Avg.|
|:--- | :---: | :---: | :---: | :---: |
|AB	|0.1875	|0.1865	|0.1826	|0.1855| 
|AC	|0.2115	|0.2074	|0.2085	|0.2091|
|AD	|0.2245	|0.2254	|0.2264	|0.2254|

数据表明，在给定固定图像大小的情况下，所提出的算法几乎需要相同的时间来提取任何长度的道路中心线。

如果我们的工作对您的研究有任何启发，请引用我们的论文：

<pre>
    该论文正在审稿中

</pre>