# template-dataset

A template for standardized MR datasets managing and processing.

*Data FAIR with elegance*

(Findable, Accessible, Interoperable, and Re-usable)

Created by Qing Wang (Vincent) @ PHI Group 
20th, Oct., 2022

## Objective
This repo will contain container recipes and run scripts to manage MR dataset organization and image processing. Currently, it offers scripts to: 
    1. Standadized data organization;
    2. Run commonly used image processing pipelines e.g. PhiPipe, FreeSurfer, fMRIPrep *etc.*
    3. Organize processed MR data inside `derivatives` directory. 

The scripts in this repo operate on a dataset directory with a specific subdir tree structure.

<img src="imgs/mr_proc_data_proc_org.jpg" alt="Drawing" align="middle" width="500px"/>

The organization of data preprocessing and processing module is as follows:
   - global_config: A json file to set various paths specific to the machine you are using which will be used for data processing. 
   - scripts: helper code to setup and check status of dataset
   - workflow: code modules to preprocess and process the dataset with stagging and logging
   - metadata: files to track dataset preprocess and process progress

## General Notes

   - The dataset setup uses Singualrity containers to run various MR image processing pipelines. Once the container is created/downloaded, you can write a python or shell run script and save them inside [my_new_pipeline](/workflow/proc_pipe/)


### 0. Setup dataset directory structure
   - This dataset template expects following directory tree with several *mandatory* subdirs and files. 
   - You can run `scripts/folder_setup.sh` to create this directory tree. 
   - You can run `scripts/folder_status.sh` check status of your dataset

<img src="imgs/mr_proc_data_dir_org.jpg" alt="Drawing" align="middle" width="1000px"/>

### 1. Create subject manifest 
   - to be detailed [People Responsible] [Time Finish]
   - Create a `participants.csv` in `<DATASET_ROOT>/tabular/demographics` comprising at least `participant_id`,`age`,`sex`,`group` (typically a diagnosis) columns.  
   - This list serves as a ground truth for subject availability and participant IDs are used to create BIDS ids downstream.
       
### 2. Gather MRI acquisition protocols (Optional)

   - to be detailed [People Responsible] [Time Finish]
   - List all the modalities and acquisition protocols used duing scanning e.g. MPRAGE, 3DT1, FLAIR, RS-FMRI etc. in the `mr_proc/workflow/dicom_org/scan_protocols.csv`
   - Although optional this is an important documentation for comparing across studies. 
   
### 3. Populate [global configs](./workflow/global_configs.json)
   - This file contains paths to dataset, pipeline versions, and containers used by several workflow scripts.
   - This is a dataset specific file and needs to be modified based on local configs and paths.

### 4. DICOM organization
   - to be detailed [People Responsible] [Time Finish]
   
### 5. BIDS conversion 
   - to be detailed [People Responsible] [Time Finish]
      
### 6. Run preprocessing pipelines
   - to be detailed [People Responsible] [Time Finish]

### 7. Run processing pipelines
   - to be detailed [People Responsible] [Time Finish]

### Known issues
   - to be detailed [People Responsible] [Time Finish]

### References

#### [mr_proc](https://github.com/neurodatascience/mr_proc) (This template is adapted from mr_proc project)

#### [PhiPipeline](https://github.com/PHI-group/PhiPipe-release)

#### [MRIQC](https://mriqc.readthedocs.io/en/stable/)

#### [SPM](https://www.fil.ion.ucl.ac.uk/spm/)

#### [TractoFlow](https://github.com/scilus/tractoflow)

#### [MAGeT Brain](https://github.com/CoBrALab/MAGeTbrain)

