#### Installation
Go to R-studio and load the R markdown file named SIMinspector_3Channel_Colocalization.Rmd containing 2 analysis scripts. 

#### Dependencies
Please install the tidyverse library.

#### How does this macro work?
In script 1/2, the user introduces microscopy parameters such as distance threshold (based on multicolour bead measurements) and the data path (‘data’) to the directory containing data coordinates of spots in three channels C1-C3 (.csv files with ‘StatisticsOfLabelmap_’ extension originating from SIMinspector_Subobject_Fiji plugin). Start script 1/2 to determine whether spots in C2 have a partner in C1.


After the script is finished, your directory ‘data’ will contain .png files (histograms) both for individual cells (grey) as well as for all cells pooled together (black). The directory will further contain .csv files with partnership measurements in binary form (1=yes, 0=no) for each analysed spot in C2. Completing script 1/2 yields two-way partnership.

To move on to three-way colocalization, run script 2/2 in order to measure partnership between spots in C2 with spots in C3.

After script 2/2 is finished, the directory will contain histograms and tables for C2 versus C3 results as well as a new .csv file containing the information of three-way partnership. In the last three columns, partnership of each analysed spot in C2 with a)C1, b)C3 and c)both C1 and C3 will be listed in binary form.
In addition, the directory will contain the three-way partnership histogram (green) for all cells. 

<img src="https://github.com/FenaOchs/Ochs_et_al.2023/blob/main/Images_Documentation/R-script%20cartoon.png" alt="Three-way colocalization scheme" width="500" height="400">

#### Note: 
As it stands, this script uses C2 as the channel used as basis for partnership search. If your dataset is structured differently, we suggest re-arranging channels in Fiji as there currently is no option to start from channels 1 or 3.

 




