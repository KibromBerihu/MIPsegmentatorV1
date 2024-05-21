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
## Results

- Two intermediate folders will be generated.

  - The resized and cropped 3D PET, and corresponding ground truth  Nifti images are saved under the folder name:
                  
      ```../output/data_default_3d_dir```, and 
  
  - The generated corresponding sagittal and coronal images are saved in the folder name       
``../output/data_default_mip_dir``.
  
  - For simplicity, the coronal PET MIP images are `pet_coronal.nii`, sagittal as `pet_sagittal.nii`, and corresponding ground truth as `ground_truth_coronal.nii`, and `ground_truth_sagittal.nii`, respectively.
  
  - NOTE: if there is no ground truth, it will only generate the coronal and sagittal PET MIPs. 
  Kindly check if these generated files are in order.
  
  
- Predicted results including predicted segmentation masks and calculated surrogate biomarekrs (sTMTV and sDmax) will be saved into the folder `output/.*`. 

 - # Predicted 2D MIP masks are saved under the folder name `output/predicted_data/final/*`. 
   
 -  # Predicted 3D masks are saved under the folder name `output/predicted_data/predicted_pseudo_3d_reconstructed/*`.  
 
- Surrogate biomarkers (sTMTV and sDmax) will be automatically calculated and saved as an EXCEL file inside the folder output/*.csv. Two EXCEL files will be saved. The first one constitutes computed surrogate biomarkers calculated from the segmentation masks predicted from AI with an indicator `predicted` in the file name. The second EXCEL file would constitute the surrogate biomarkers computed from the reference segmentation masks (i.e., ground truth) from the expert (if available) with an indicator `ground_truth` in the file name. In addition to the `predicted` and `ground truth` indicator names, the CSV file's name also constitutes an automatically generated month, year, and the processing time.
- 
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
