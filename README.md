This repository contains the materials associated with the publication "Sister chromatid cohesion is mediated by individual cohesin complexes" by Ochs et al., 2023.

#### List of scripts
1) SIMinspector_Mainobject_Fiji: Documentation and script [here](https://github.com/FenaOchs/Ochs_et_al.2023/tree/main/1)SIMinspector_Mainobject_Fiji)  
2) SIMinspector_Subobject_Fiji: Documentation and script [here](https://github.com/FenaOchs/Ochs_et_al.2023/tree/main/2)SIMinspector_Subobject_Fiji)
3) SIMinspector_3Channel_Colocalization: Documentaton and script [here](
https://github.com/FenaOchs/Ochs_et_al.2023/tree/main/3)SIMinspector_3Channel_Colocalization_R)

#### What is SIMinspector?
SIMinspector is an image analysis pipeline that allows studying spatial relationship between spots identified in 3D super-resolution Structured Illumination Microscopy (SIM) images. Specifically, it allows the analysis of partnership between nuclear spots of interest and other spots (up to 2 more species) based on spatial proximity. 
SIMinspector as a pipeline was developed to i) identify positions of spots within multicolour 3D SIM images of cell nuclei (up to 3 spot species in 3 respective channels) and ii) analyse two- or three-way partnership between those spot species.

#### How does it work?
SIMInspector consists of the following entities: i) two Fiji/ImageJ scripts, and ii) R-Studio markdown containing a pair of scripts. Both files are required to perform the partnership analysis provided by SIMInspector and must be used in the right order that is:

#### Step 1/3: Segment the main object (cell nucleus)
In a first step the Fiji script “SIMinspector_Mainobject_Fiji” segments the main object in the provided image based on intensity thresholding and Gaussian blurring. This allows removal of spots outside the region of interest. This script also crops the image to the main object to allow for faster processing in subsequent steps. The output of this script are processed images.

#### Step 2/3: Identify subobjects (spots in nucleus)
In order to identify subobjects in up to three channels inside the segmented main objects, intensity thresholding and water-shed based segmentation of spot signals is used in the Fiji script “SIMinspector_Subobject_Fiji”. This script produces .csv files containing information on subobjects in each channel including volume, intensity and center position measurements. It further yields two-way partnership measurements based on voxel overlap and distance measurements.

#### Step 3/3: Investigate spatial relationship and estimate spot partnership
Go to R-studio and load the R markdown file named SIminspector_3Channel_Colocalization.Rmd containing 2 analysis scripts that will work on the 3 channel-specific .csv files generated in the previous step. Script 1/2 analyses for each spot in C2 whether a partner in C1 exists. Script 2/2 repeats this process to search for a partner in C3. This script produces histograms for individual and pooled input data as well as a .csv file containing information on two-way and three-way partnership in binary form.

