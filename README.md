# MIPsegmentatorV1
 [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 
 [![Docker build passing](https://img.shields.io/badge/docker%20build-passing-brightgreen)](https://github.com/KibromBerihu/ai4elife/blob/main/Dockerfile) 

## *Artificial Intelligence for Efficient Learning-based Image Feature Extraction.*
Tool for detecting and segmenting lesions in 3D whole-body PET images with automated quality control. It was trained on lymphoma data, including the AutoPET data. First, it automatically detects and segments lesion areas on the coronal and sagittal maximum intensity projections (MIP) PET images. A 3D lesion segmentation reconstruction algorithm is then developed to obtain the 3D lesion from the two 2D MIP segmentations using the SUV values from the 3D PET images.

If you use this pipeline, please cite our [JNM paper](https://doi.org/10.2967/jnumed.121.263501) and the [autopet data](https://doi.org/10.1038/s41597-022-01718-3) paper. For additional information regarding the AI-based lesion segmentations from the coronal and sagittal maximum intensity projections (MIP) PET images, please refer to the [github code](https://github.com/KibromBerihu/ai4elife). 

This tool provides 2D MIP and 3D lesion segmentation on whole-body PET images, including automated quality control. The input 3D PET image should be in SUV NIFTI format. 

<div align="center">
 <img src="https://github.com/KibromBerihu/MIPsegmentatorV1/blob/main/images/mipsegmentator.jpg" />
</div>

## Required input folder structure
Please provide all data in a single directory. The method automatically analyses all given data batch-wise. 

To run the program, you only need PET scans (CT is not required) of patients in nifty format, where the PET images are coded in SUV units. If your images have already been segmented, you can also provide the mask (ground truth (gt)) as a binary image in nifty format. Suppose you provided ground truth (gt) data; it will print the dice, sensitivity, and specificity metrics between the reference segmentation by the expert (i.e., gt) and the predicted segmentation by the model. If the ground truth is NOT AVAILABLE, the model will only predict the segmentation. 

A typical data directory might look like:


    |-- main_folder                                             <-- The main folder or all patient folders (Give it any NAME)

    |      |-- parent folder (patient_folder_1)             <-- Individual patient folder name with unique id
    |           |-- pet                                     <-- The pet folder for the .nii suv file
                     | -- name.nii or name.nii.gz            <-- The pet image in nifti format (Name can be anything)
    |           |-- gt                                      <-- The corresponding ground truth folder for the .nii file  
                     | -- name.nii or name.nii.gz            <-- The ground truth (gt) image in nifti format (Name can be anything)
    |      |-- parent folder (patient_folder_2)             <-- Individual patient folder name with unique id
    |          |-- gt                                     <-- The pet folder for the .nii suv file
                    | -- name.nii or name.nii.gz            <-- The pet image in nifti format (Name can be anything)
    |         |-- pet                                      <-- The corresponding ground truth folder for the .nii file  
                    | -- name.nii or name.nii.gz            <-- The ground truth (gt) image in nifti format (Name can be anything)
    |           .
    |           .
    |           .
    |      |-- parent folder (patient_folder_N)             <-- Individual patient folder name with unique id
    |           |-- pet                                     <-- The pet folder for the .nii suv file
                    | -- name.nii or name.nii.gz            <-- The pet image in nifti format (Name can be anything)
    |           |-- gt                                      <-- The corresponding ground truth folder for the .nii file  
                    | -- name.nii or name.nii.gz            <-- The ground truth (gt) image in nifti format (Name can be anything)


 **Note:** the folder name for PET images should be `pet` and for the ground truth `gt`. All other folder and sub-folder names could be anything.

## Usage
 <font size ="4"> For reproducibility purposes, the method is currently available only in a Docker image.</font> <br/><br>
   1) Assuming you already have [docker desktop](https://www.docker.com/) installed. For more information, kindly refer to [THIS](https://docs.docker.com/).
   2) `Docker pull kibromberihu/mipsegmentator:latest-0`
   3) `docker run -v "/path/to/input_output/input/":"/home/docker_input" -v  "/path/to/input_output/output/":"/home/docker_output" kibromberihu/mipsegmentator:latest-0 `
## Results  
- Predicted results including predicted segmentation masks and calculated surrogate biomarekrs (sTMTV and sDmax) will be saved into the folder `output/.*`. 

 - Predicted 2D MIP masks are saved under the folder name `output/predicted_data/final/*`. 
   
 - Predicted 3D masks are saved under the folder name `output/predicted_data/predicted_pseudo_3d_reconstructed/*`.  
 
- Surrogate biomarkers (sTMTV and sDmax) will be automatically calculated and saved as an EXCEL file inside the folder output/*.csv. Two EXCEL files will be saved. The first one constitutes computed surrogate biomarkers calculated from the segmentation masks predicted from AI with an indicator `predicted` in the file name. The second EXCEL file would constitute the surrogate biomarkers computed from the reference segmentation masks (i.e., ground truth) from the expert (if available) with an indicator `ground_truth` in the file name. In addition to the `predicted` and `ground truth` indicator names, the CSV file's name also constitutes an automatically generated month, year, and the processing time.

## Citations 
Please consider citting the following papers if you use this package for your research:
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
