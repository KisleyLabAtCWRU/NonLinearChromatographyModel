# NonLinearChromatographyModel
Code for "The non-linear effects of the number of stochastic single-molecule adsorption events on ensemble elution profiles" DOI: 10.1039/D6AN00199H 

Modified version of the Levy process representation of the stochastic theory of chromatography, developed by Pasti et al. (DOI: 10.1021/AC0482514), implemented in Matlab (2024a) with error minimization options.

See DOI: 10.1039/D6AN00199H  for more details.

Instructions:

    Download code package into Matlab accessible directory.
    Open the Main code: Pasti_etal_ErrorFitting_vUpload.mat
    Define user defined parameters: dt=30; % avg. time between frames in ms (exposure + clean time); numFrames=2000; %total number of frames per collection - for possible observed times; Weights = [1,1,1];% [Asymmetry, Width, Elution time] - error minimization weight values runMinimization = 0; %if '1' runs error minimizer; if '0' defaults to theoretical rm value
    Run code by sections
    Select files containing SM observables
    Select Excel file containing HPLC to compare to, if applicable
    Run final section
    Output: peakStore - output chromatograms and shape parameters

rZ -1 = matches selected SM observable dataset file order peakStore(rZ-1).Model ([model peak time points; model peak signal; normalized model peak signal; centered time axis for model peaks]);%in minutes scale peakStore(rZ-1).LinearVel = linear veloctity if specified peakStore(rZ-1).dTmodel = dTmodel/60; %time step between data points, given in minutes peakStore(rZ-1).fitError = error fitting output peakStore(rZ-1).rmFit = obtained rm value used or fitted to peakStore(rZ-1).rmTheory = rm calculated based on theory by HPLC elution time peakStore(rZ-1).meanDwell = mean single molecule adsorption time;% in units of ms peakStore(rZ-1).asym = asymetry factor peakStore(rZ-1).wR = peak width, using 10% singnal tangent method peakStore(rZ-1).tR = elution time of model peak peakStore(rZ-1).pMax = model peak maximum
