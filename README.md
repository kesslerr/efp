# efp
emotional face processing project

The paradigm is described in Kessler et al. (2021). The data here corresponds to "paradigm A" or "study A" which is described in the paper for more detail.

The functional data in this repository has been preprocessed (see below), including spatial normalization. For the data used in the manuscript (Kessler et al. 2021) no spatial normalization has been applied.

## experiment
To investigate brain connectivity during the observation of different basic emotions, a paradigm was designed to present image sequences of neutral, happy, angry, or fearful faces as well as houses in a block design. The face stimuli (39 individuals) were taken from the Radboud Face Database (RaFD, (Langner et al., 2010)), whereas the house stimuli were freely available pictures taken from the internet. Stimuli were transformed into gray-scale images and cropped to 500*400px. Furthermore, they were matched in mean luminance using SHINE toolbox for MATLAB (Willenbockel et al., 2010). To avoid lateralization effects due to low level image properties like asymmetries in the faces or houses, each image was mirrored vertically in one half of its appearances. In the center of each stimulus, as well as during the inter-stimulus-intervals and inter-block-intervals, a fixation cross was shown in the center of the screen. Participants were advised to maintain fixation during the entire experiment. Each of the five conditions appeared 20 times, resulting in a total of 100 blocks. Within each block, a sequence of 24 images was shown - 350ms face or house stimulus followed by 150ms fixation cross - resulting in a total block length of 11.85s (main article, Fig. 2). Between the blocks, a jittered inter-block-interval of 3.3 to ∼7.3 seconds was introduced to reduce anticipation effects. Additionally, four pause-trials of 25 seconds were included, appearing after the 21st, 40th, 60th, and 80th stimulus block, in which participants were instructed to relax and close their eyes. To ensure the attention of the participants during stimulus presentation, a 1-back task was introduced. Participants were instructed to indicate were instructed to press a button with the index finger of both hands whenever a stimulus was shown twice in a row, which happened 1-3 times in each block. Total duration of the experiment was about 30 minutes.

## fmri scan
All MRI data were acquired at a 3.0-Tesla MR scanner (Siemens TIM Trio, Erlangen, Germany) using a 12-channel head matrix receive coil at the Core Unit Brainimaging, Department of Psychiatry and Psychotherapy, University of Marburg. A high-resolution structural data set was acquired using a T1 weighted magnetization prepared rapid gradient echo (MPRAGE) sequence with the following parameters: acquisition time (TA) 4:18 min, repetition time (TR) 1900 ms, echo time (TE) 2.52 ms, field of view (FoV) 256 mm, matrix 256x246, slice thickness (ST) 1 mm, phase encoding direction (PE) anterior » posterior, distance factor (DF) 50 %, flip angle 9°, parallel imaging GRAPPA with acceleration factor 2, bandwidth 170 Hz/Px, sagittal, ascending acquisition, 176 slices.
Functional images were collected using a T2*-weighted gradient-echo echo-planar imaging sequence (EPI) sensitive to Blood Oxygen Level Dependent (BOLD) contrast. TR 1550 ms, TE 36 ms, FoV 200 mm2, matrix 72x72, phase oversampling 12 %, ST 2.7 mm, DF 15 %, voxel size: 2.8x2.8x2.7 mm (2.8x2.8x3.1 mm incl. gap), PE anterior » posterior, flip angle 70 °, bandwidth 1654 Hz/Px, no parallel imaging, ascending acquisition, 20 slices with the measurement volume aligned to the AC-PC-line (anterior commissure to posterior commissure). The volume covered the whole temporal and occipital lobes and the IFG.


## preprocessing
All fMRI data sets were analyzed using the Statistical Parametric Mapping software (SPM12, release 6685, Welcome Department of Cognitive Neurology, Institute of Neurology, London, United Kingdom) based on MATLAB (version 8.3 R2014a). The initial three functional images were excluded from further analysis due to T1 stabilization effects, as implemented in the protocol of the MR scanner system. Fieldmaps were calculated using the acquired phase and magnitude images from a fieldmap sequence. These were converted to voxel displacement maps to unwarp geometrically distorted EPI images. In a combined realign & unwarp step, the effects of static and movement-related susceptibility induced distortions were corrected for, as well as within-participant motion correction through a rigid body (6 parameters) spatial transformation. Each participant’s functional images were also normalized to Montreal Neurological Institute (MNI) space. To end up with an accurate transformation, each participant's T1 weighted image (coregistered to the mean functional image) was segmented, bias corrected, and spatially normalized using the segmentation algorithm as implemented in SPM12 (formerly called "New Segment" in SPM8). The resulting forward deformation field was used for registering the realigned functional images to MNI space that subsequently were resampled to a resolution of 2*2*2 mm and blurred with an isotropic Gaussian filter of 6mm FWHM.


## first level analysis
Statistical analyses were performed within a general linear model (GLM) framework to create a 3-dimensional map in relation to the estimated regressor response amplitude. At the single participant level, the task was modeled in a block design with BOLD responses for each condition (neutral, happy, angry, and fearful faces as well as houses, respectively) convolved with the canonical hemodynamic response function. Inter-block-intervals and breaks was not modeled. The six realignment parameters of the motion correction procedure were included in the statistical model as nuisance regressors to correct for residual head movement. For each participant, brain activation differences between face conditions and control conditions were calculated. High pass filtering was applied with a cut-off frequency of 1/256 Hz to attenuate low frequency components. At the group level, the weighted ß-images (face conditions vs. control condition) were entered into one-sample t-tests.

Each subject folder contains the corresponding SPM.mat file and several contrast images and t-maps.
The contrast index are as follows:
- 1 EOI (F-Contrast)
the following are t-contrasts:
- 2 Faces
- 3 Houses
- 4 Happiness
- 5 Anger
- 6 Fear
- 7 Faces > Houses
- 8 Faces+Happiness > Houses
- 9 Faces+Anger > Houses
- 10 Faces + Fear > Houses
- 11 Happiness > Houses
- 12 Anger > Houses
- 13 Fear > Houses
- 14 Houses > Faces
- 15 Visual Input + Emotions
- 16 Faces + Happiness > Houses
- 17 Faces + Anger > Houses
- 18 Faces + Fear > Houses
- 19 Positive > Negative Emotions
- 20 Negative > Positive Emotions
- 21 Approach > Withdrawal Emotions
- 22 Withdrawal > Approach Emotions
- 23 Visual Input along
(yes: some contrasts are redundant).

## Time series
Time Series were extracted for different ROIs (adjusted for the EOI contrast) in all Voxels active at the faces>houses contrast (threshold = 0.001). The corresponding files have prefix "VOI_".

