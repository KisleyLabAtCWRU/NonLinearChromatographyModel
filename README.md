# NonLinearChromatographyModel
Code for "The non-linear effects of the number of stochastic single-molecule adsorption events on ensemble elution profiles" DOI: 10.1039/D6AN00199H 

Modified version of the Levy process representation of the stochastic theory of chromatography, developed by Pasti et al. (DOI: 10.1021/AC0482514), implemented in Matlab (2024a) with error minimization options.

Instructions (also in uploaded ReadMe_Instructions.txt):
Kisley Lab - Levy Process Representation of Chromatography
	Authors: Ricardo Monge Neria, Rachel A. Saylor, Lydia Kisley	Guide - 5.15.26
	Code - 2025; MATLAB 2024a

Based on:
	Pasti, et al., doi: 10.1021/AC0482514

Data needed to evaluate the conclusions in the paper:
	Present at Zenodo https://doi.org/10.5281/zenodo.13697196
	and
	https://doi.org/10.1126/sciadv.ads0790
	Additional data is available upon request from lydia.kisley@case.edu

LRG_SuperResLocalization Code details can be found in: 
	GitHub - KisleyLabAtCWRU/SuperResKinetics: 
	Super-resolution imaging and single molecule kinetics MATLAB analysis, 	https://github.com/KisleyLabAtCWRU/SuperResKinetics used for obtaining single molecule locations and dwell time values that are fed into the Levy Process code

Subfolders description:
	HPLC:
		-Data from HPLC runs of rhodamine6G on Cellulose-B columns at varying flow rates
		-Included as averaged values for 3x duplicates, with standard deviations
	LevyProcess:
		- Functions used for the Levy Process model
		- Run these only after running through LRG code

Note: If at any point in running code you run into 'could not find file' errors, make sure to update the file paths in the code/MATLAB scripts to match your folder locations.
	-Look for the "startlocat" and "mainFolderLocat" variables

Also, run LevyProcess code by Section rather than full script for best use.

Analyzis procedure:

	1) Run the .tif files microscopy image data through the KisleyLabAtCWRU/SuperResKinetics code packages
		1a) find KisleyLab_LevyModelChromatography\RM_LRG_ParametersTest.mat
			-run this code to test the parameter settings for the localization code for your data
		1b) once chose parameters work, run full data sets through LRG_SuperRes_Main.m
			-this will generate output "_analyzed.mat" files
		
	2) Find and open LevyProcessModelFunctions\Pasti_etal_ErrorFitting_vUpload2.mat
		- Define the need user parameters in lines  13-17	
		- Update "startloc" to the subfolder where your "_analyzed.mat" data is stored
		- Look at the Optional cumulative and dwell time distribution sections -> uncomment and run if not done already
		- Update the "readtable" file location in line 80 to match location of HPLC data sheet
		- use "runMinimization = 0" in line 17 if want to skip error minimization fitting
		- LevyModelElution_error_vUpload.mat function calculates error between model and HPLC data
		- levyElutionModel.mat generates model chromatograms based on dwell times, rm value, and user parameters
	
-Pasti_etal_ErrorFitting_vUpload2.mat is the main code for the model chromatograms fitting analysis

-levyElutionModel.mat is the code that generates the chromatograms

