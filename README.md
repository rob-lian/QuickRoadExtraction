# A Quick Road Centerline Extraction Method from High-resolution Remote Sensing
### Abastract 
Quickly extracting road networks from high-resolution remote sensing images is crucial in mapping, urban planning, and GIS databases updating. Semi-automatic road extraction, as the main method of road surveying and mapping, is a labor-intensive task. In order to reduce the cost of manual intervention and improve work efficiency, this paper proposes a fast road centerline extraction algorithm that combines an adaptive circular template and geodesic distance. First, the best circular templates are automatically estimated using the improved morphological gradient map, and the artificial seeds are adjusted to road center at the same time, and then the road saliency map is calculated according to the local color features inside the templates. After that, the soft road center probability density is estimated that is used to compute the geodesic lines. the geodesic lines between the continues seeds are extracted using fast sweep scan followed by the curve smoothing using mean filter and finally obtain the smooth road center lines. Extensive experiments and quantitative comparisons show that the proposed algorithm can greatly reduce manual intervention without losing much accuracy, and significantly improve the efficiency of road extraction. Moreover, the proposed algorithm takes almost the same time to extract any length of road centerline given a fixed image size, and no hyperparameters need to be set. The algorithm behaves good experience in human-computer interaction.

### Dataset
We use [Google Earth](http://www.escience.cn/people/guangliangcheng/Datasets.html) to evaluation the performance of our method.

<!--
### Method

#### Adaptive circle generation

Step 1: Take the seed point as the center O of the current best circular template, and set the radius r to 1;  
Step 2: Generate nine circles with a radius of r by taking the Jiugong grid with O as the center as the center;  
Step 3: Calculate the morphological gradient sum within the coverage of each circle, and set the minimum circle center of the gradient sum as O’ and the gradient sum as S;  
Step 4: If S is greater than r, go to step 6, otherwise let O be equal to O’ and r be equal to r+1;  
Step 5: If r is greater than the maximum template radius, go to step 6, otherwise, go to step 2;  
Step 6: Output O and r  

#### Quick extract road centerline  
input:  
Seed point, probability density of road center  
Step 1: Initialize the distance field U and cost matrix C;  
Step 2: Scan U and C iteratively according to Gauss-Seidel; update U according to formula (10) in the paper during scanning;
Step 3: Let Path=[xe], x=xs where xs is the start seed and the xe is the end seeds;  
Step 4: Let U(x’) be the smallest distance in the 8 areas of x, add x’ to Path, let x=x’;
Step 5: If x=xs, go to output, otherwise go to step 4.  
Output:  
Path  
-->
### Experiment results

#### Extract demo
The videos show the procedure of some test cases.  
coming soon  

The demonstrations show that we do not need to sed any hyperparameter to run our algorithm.
#### Extraction results
We post some test cases here to demonstrate the effective of our method.  
<p>
    <img src='images/image1.jpg?raw=true' />
</p>
<p>
    <img src='images/image8.png?raw=true' />
</p>
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
    <img src='images/image92.png?raw=true' />
</p>
<p>
    <img src='images/image141.png?raw=true' />
</p>
<p>
    <img src='images/image155.jpg?raw=true' />
</p>
<p>
    <img src='images/image173.jpg?raw=true' />
</p>
<!--
### Performance
*The extraction results show the superiority of the algorithm Visually. We can further show the performance using serval indics. The performances of road extraction methods are often measured by completion, accuracy, and quality, but semi-automatic algorithms can always improve these three indicators by increasing the degree of manual intervention. Therefore, we introduced other indicators as follows  
*Completion (COM), Correct (CORR), Quality: COM=TP/(TP+FN), CORR=TP/(TP+FP), Quality=TP/(TP+FN+ FP)  
*Seed Number(Seeds): Which reflects the number of manual interactions required by the algorithm.  
*Segment Number(Segments): Which reflects the intelligence of the algorithm. The more segments, the shorter the distance between the seed points and the lower the intelligence of the algorithm.
*Average response delay (Delay): Which reflects the sensitivity of the algorithm. The smaller of this indicator means the better.  
*Total time (Time): The total time from the start of the extraction to the end of the extraction, including the time consumption of algorithm, undo and redo, human-computer interaction, etc., which reflects the overall efficiency of the method  
-->
### Times Consuming  
The experimental operating environment is a 4-core 1.8GHz i7 processor, a notebook with 16G memory, the implementation language is Python3.7, and the iteration part of the three algorithms is accelerated by numba  
We Extract three road centerlines of different lengths. As shown in below, the three road sections are AB, AC, and AD, and the road lengths are about 480 meters, 990 meters, and 1310 meters, respectively.
<p>
    <img src='images/Fig8-c.png?raw=true' />
</p>  
Make data more credible, we extract three times for each segment. The Time Consuming are shown as below  

|segment|1st|2nd|3th|Avg.|
|:--- | :---: | :---: | :---: | :---: |
|AB	|0.1875	|0.1865	|0.1826	|0.1855| 
|AC	|0.2115	|0.2074	|0.2085	|0.2091|
|AD	|0.2245	|0.2254	|0.2264	|0.2254|

The data shows that the proposed algorithm takes almost the same time to extract any length of road centerline given a fixed image size.

If our work has any inspiration for your research, please cite our paper:

<pre>
    The paper is undergoing review

</pre>