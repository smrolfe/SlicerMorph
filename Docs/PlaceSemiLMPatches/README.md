## PlaceSemiLMPatches
**Summary:** This utility module applys a connectivity table generated by the `CreateSemiLMPatches` module to place semi-landmarks on new 3D models using the patch placement method described in the `CreateSemiLMPatches` module. All models are required to have the same set of anatomical landmarks. Using this method, the semi-landmark placement on each subject is independant of the rest of the data set and the initial template used to generate the connectivity table.

### USAGE 

#### PlaceSemiLMPatches PARAMETERS

* __Mesh Directory:__ Selects the directory containing the models that for semi-landmarking.

* __Landmark Directory:__ Selects the directory containing the fixed anatomical landmarks of the models for semi-landmarking in `.fcsv` format. Each model and its corresponding landmark file should have the same filename prefix.

* __Grid connectivity file:__ Selects the table created by the `CreateSemiLMPatches` module and stored as a `.csv` file. This file contains the the fixed landmark numbers that form the vertices of each triangular patch in the semi-landmarking set.

* __Output directory:__ Selects the directory where the output semi-landmarks for each subject will be stored as a `.fcsv` file.

* __Sample rate for interpolation:__ This value sets the number of resampling row/columns in each patch and is used to control the number of semi-landmark points placed. Unlike `CreateSemiLMPatches`, this value can not be changed over sampling patches or subjects.

#### LIMITATIONS
* This module provides the benefit of independent semi-landmark placement that is not biased by the choice of a reference model. However, in cases where there is large morphological differences between samples or mesh quality issues (i.e. holes, noise), generating a semi-landmark grid on a representative sample may not be a good prediction of how the module will perform on other images.

* The point placement should be evaluated before semi-landmarks are used for shape analysis.

* If points are not placed in corresponding regions across images, the `ProjectSemiLM` or `Alpaca` modules can provide a more robust alternative for transferring the semi-landmarks from the original patch-placed set.


### TUTORIAL
For more information of generating the connectivity table used by the `PlaceSemiLMPatches` module, please see the [CreateSemiLMPatches tutorial](https://github.com/SlicerMorph/S_2020/blob/master/Day_3/Patch-based_semiLMs/Patch-based_semiLMs.md).





