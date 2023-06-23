The aim of this macro is to segment the nucleus, mask it, crop the image then save it.


### Important:
This macro will assume that the largest object in the image is the nucleus that needs to be saved. If there is more that one nucleus per image then only the largest one will be kept. If you have more than one nucleus then simply either loose one or separate them before running the macro.

## Installation
Download [this file](https://github.com/FenaOchs/Ochs_et_al.2023/releases/download/v1/SIMinspector_Mainobject_Fiji.ijm). Then in Fiji go to `Plugins > Install...`, select the newly downloaded file and save in your Fiji Plugins folder. 
`SIMinspector_Mainobject_Fiji` will then appear in your Plugins menu.

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


## How does this macro work?
When running the macro the first step is to populate the dialog:

<img src="https://github.com/FenaOchs/Ochs_et_al.2023/blob/main/Images_Documentation/Macro1_dialog.png" alt="DialogMacro1" width="492" height="549">

* You need to choose the directory that contains the images to mask. (No other files should be in that directory!)
* Choose a different folder where the new masked images will be saved.
* Select the channels used to create the mask.
* A Gaussian blur is applied on the selected channel before thresholding. Set the desired value (default is 10)
* Set the threshold (see below for “How do I know which parameters to use”)
* Define how much space will be left around the nucleus after cropping (0 is usually sufficient because of the blur)




Final options:
* Pause macro at the end of each file: This is useful when optimising the settings and to ensure all is working as expected. This will display the main images in the workflow (start and end).
* Show Intermediary images: this will display all intermediary images. Good for optimising parameters.
* Save log with settings: This will save a small text file with the settings selected in the dialog.
## Overview of the workflow:

<img src="https://github.com/FenaOchs/Ochs_et_al.2023/blob/main/Images_Documentation/Macro1_workflow_diagram.png" alt="MacroWorkflow" width="634" height="1303">

#### For the last release of this project follow this [link](https://github.com/LiorPytowski/SIMinspector)
