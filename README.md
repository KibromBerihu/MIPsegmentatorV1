# MIPsegmentatorV1
 [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 
 [![Docker build passing](https://img.shields.io/badge/docker%20build-passing-brightgreen)](https://github.com/KibromBerihu/ai4elife/blob/main/Dockerfile) 

## *Artificial Intelligence for Efficient Learning-based Image Feature Extraction.*
Tool for detecting and segmenting lesion in 3D PET images and automated quality control.  It was trained on lymphoma data including the autopet data. 
If you use it please cite our [JNM paper](https://doi.org/10.2967/jnumed.121.263501) and the [autopet data](https://doi.org/10.1038/s41597-022-01718-3) paper.
For the file structure and additional information please refer to the [github code](https://github.com/KibromBerihu/ai4elife).
The input 3D PET image is should be in SUV NIFTI format. A 3D lesion segmentation on whole-body PET images including automated quality control.



## Installation <a name="installation"> </a>
MIPsegmentator works on Ubuntu, and Windows and on CPU and GPU. Not tested on mac. 
Install depenencies:

	-  Python >= 3.6

	-  Keras >= 2.3.1

	-  Tesnsorflow >=2.1.0



## usage
 <font size ="4"> Using docker image: building image from docker file [REPRODUCIBLE] </font> <br/><br>
   1) Assuming you already have [docker desktop](https://www.docker.com/) installed. For more information, kindly refer to [THIS](https://docs.docker.com/). 
      
   2) Docker pull kibromberihu/mipsegmentator:latest-0
      <br/><br>
   3) docker run -v "/path/to/input_output/input/":"/home/docker_input" -v  "/path/to/input_output/output/":"/home/docker_output" kibromberihu/mipsegmentator:latest-0
   <br/><br>

## Citations 
Please cite the following papers if you use this package for your research:
```
   1. DOI: https://doi.org/10.2967/jnumed.121.263501 
```
```
   2. DOI: https://doi.org/10.1109/TMI.2021.3060497
```
```
   3. DOI: https://doi.org/10.1038/s41597-022-01718-3
```
## Acknowledgments
We thank you [the reader].  
