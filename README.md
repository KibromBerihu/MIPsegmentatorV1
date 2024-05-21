# MIPsegmentatorV1
 [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 
 [![Docker build passing](https://img.shields.io/badge/docker%20build-passing-brightgreen)](https://github.com/KibromBerihu/ai4elife/blob/main/Dockerfile) 

## *Artificial Intelligence for Efficient Learning-based Image Feature Extraction.*
Tool for detecting and segmenting lesion in 3D PET images and automated quality control.  It was trained on lymphoma data including the autopet data. First, it autmatically 
detects and segments lesions areas on the coronal and sagittal maximum intensity projections (MIP) PET images. A 3D lesion segmentation reconstruciton algorithm is then developed to get
the 3D lesions areas from the two 2D MIP segmentations thanks to the SUV value from the 3D PET images. 
If you use this pipeline please cite our [JNM paper](https://doi.org/10.2967/jnumed.121.263501) and the [autopet data](https://doi.org/10.1038/s41597-022-01718-3) paper.
For the file structure and additional information please refer to the [github code](https://github.com/KibromBerihu/ai4elife).
The input 3D PET image is should be in SUV NIFTI format. A 3D lesion segmentation on whole-body PET images including automated quality control.

## usage
 <font size ="4"> For reproducibility purposes, the method is currently available only in a Docker image.</font> <br/><br>
   1) Assuming you already have [docker desktop](https://www.docker.com/) installed. For more information, kindly refer to [THIS](https://docs.docker.com/).
   2) `Docker pull kibromberihu/mipsegmentator:latest-0`
   3) `docker run -v "/path/to/input_output/input/":"/home/docker_input" -v  "/path/to/input_output/output/":"/home/docker_output" kibromberihu/mipsegmentator:latest-0 `
      	 
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
