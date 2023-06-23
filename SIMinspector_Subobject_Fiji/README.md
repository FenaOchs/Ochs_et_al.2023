The aim of this macro is to segment foci in 2 channels then measure certain coloc-related parameters. It was designed to be used after Macro_1 although it may not be essential.


## Installation
Download [this file](https://github.com/FenaOchs/Ochs_et_al.2023/releases/download/v1/SIMinspector_Subobject_Fiji.ijm). Then in Fiji go to `Plugins > Install`, select the newly downloaded file and save in your Fiji Plugins folder. 
`SIMinspector_Subobject_Fiji` will then appear in your Plugins menu.


## Dependencies
:heavy_exclamation_mark: The macros need certain update sites plus a manually installed plugin to run.

The update sites are:
* 3D ImageJ Suite
* Java8
* CLIJ
* CLIJ2
* clijx-assistant
* clijx-assistant-extensions
* IJPB-plugins
* ImageScience

See this [tutorial to learn how to add update sites to ImageJ](https://imagej.net/update-sites/following).

:heavy_exclamation_mark:  Additionally please install `DiAna 1.50`. The latest version of DiAna can be found [here](https://imagej.net/plugins/distance-analysis#installation). An archived copy of `DiAna 1.50` is also in [this repository](https://github.com/FenaOchs/Ochs_et_al.2023/tree/main/SIMinspector_Subobject_Fiji/DiAna_1.50).
To install please download the `.jar` file the place it in the `plugins` folder of your fiji installation. (In Windows, simply navigate with the File Explorer; in Mac, right click the FIJI app then select `Show Package Contents` then navigate to the plugins folder)


### FAQ
#### How do I know what parameters to use when running the macro for the first time?
Run the macro with the default settings and make sure to select the options to pause the macro at the end of each file and show all the intermediary results.

Once you have that inspect the images and check whether the parameters seem correct. If not, then try different thresholds for example then re-run the macro with the newly selected thresholds.
#### What are the units of the measurement outputs?
Measurements in “StatisticsOfLabelmap” files are **not** calibrated.

Measurements in “AdjacencyResults” and “ColocResults” are calibrated meaning that they use the same units present in the properties of the image. (The menu path to check image properties in Fiji is: Image › Properties...).

All distance measurements are based on the geometric centers except for the measurements in the “AdjacencyResultsCentersofMass” files that use the centers of mass. 

### How does this macro work?
When running the macro the first step is to populate the dialog:

<img src="https://github.com/FenaOchs/Ochs_et_al.2023/blob/main/Images_Documentation/Macro2_dialog.png" alt="MacroWorkflow" width="759" height="1155">

* You need to choose the directory that contains the images to process. ( This would be the output of the macro 1. No other files should be in that directory!)
* Choose a different folder where the results will be saved.
* Choose the channels to segment and measure distances. Channel A will be the reference channel.
* Choose the segmentation algorithms.
* Choose the minimum and maximum spot sizes included in the analysis.
* Choose how many neighbouring objects will be used to compute the distances

Additional options:
* Pause macro at the end of each file: This is useful when optimising the settings and to ensure all is working as expected. This will display the main images in the workflow (start and end).
* Show Intermediary images: this will display all intermediary images. Good for optimising parameters.
* Save log with settings: This will save a small text file with the settings selected in the dialog.

Advanced options:
* Radius for the detection of maxima. The maximas are used as seeds for the watershed. The lower the value the more object will be in the final label map.
* Depending on the segmentation algorithm used you may want to erode the labels.

### Additional details regarding the workflow:

<img src="https://github.com/FenaOchs/Ochs_et_al.2023/blob/main/Images_Documentation/Macro2_workflow_diagram.png" alt="MacroWorkflow" width="862" height="1079">

### Outputs:
For each image 5 files are generated.  
They are:

* *Filename*@AdjacencyResultsCentersOfMass_C2vsC1.csv
	* This will have the following measurements:
		* Dist CenterA-CenterB.
* *Filename*@AdjacencyResultsGeometricCenters_C2vsC1.csv
	* This will have the following measurements:
		* Dist CenterA-CenterB
		* Dist min EdgeA-EdgeB
		* Dist min CenterA-EdgeB
		* Dist min EdgeA-CenterB.

* *Filename*@ColocResults_C2vsC1.csv
	* This will have the following measurements:
		* OverlapVolume(pxl)
		* ColocFromAvolume
		* ColocFromBvolume
		* ColocFromABvolume
		* Dist CenterA-CenterB
		* Dist min CenterA-EdgeB
		* Dist min EdgeA-CenterB

* *Filename*@StatisticsOfLabelmap_C1.csv
* *Filename*@StatisticsOfLabelmap_C2.csv
	* This will have the following measurements:
		* IDENTIFIER
		* BOUNDING_BOX_X
		* BOUNDING_BOX_Y
		* BOUNDING_BOX_Z
		* BOUNDING_BOX_END_X
		* BOUNDING_BOX_END_Y
		* BOUNDING_BOX_END_Z
		* BOUNDING_BOX_WIDTH
		* BOUNDING_BOX_HEIGHT
		* BOUNDING_BOX_DEPTH
		* MINIMUM_INTENSITY
		* MAXIMUM_INTENSITY
		* MEAN_INTENSITY
		* SUM_INTENSITY
		* STANDARD_DEVIATION_INTENSITY
		* PIXEL_COUNT
		* MASS_CENTER_X
		* MASS_CENTER_Y
		* MASS_CENTER_Z
		* CENTROID_X
		* CENTROID_Y
		* CENTROID_Z
		* SUM_DISTANCE_TO_MASS_CENTER
		* MEAN_DISTANCE_TO_MASS_CENTER
		* MAX_DISTANCE_TO_MASS_CENTER
		* MAX_MEAN_DISTANCE_TO_MASS_CENTER_RATIO
		* SUM_DISTANCE_TO_CENTROID
		* MEAN_DISTANCE_TO_CENTROID
		* MAX_DISTANCE_TO_CENTROID
		* MAX_MEAN_DISTANCE_TO_CENTROID_RATIO
		
		
#### For the last release of this project follow this [link](https://github.com/LiorPytowski/SIMinspector).
