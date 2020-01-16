# efp
emotional face processing project

## experiment
This was an fMRI experiment, with subjects laying in the scanner and seeing blocks of either faces (neutral (20% probability), happy  (20% probability), angry (20% probability) or fearful (20% probability) expression) or houses (20% probability). The exact data analysis can be found here: *** to do ***

## fmri scan
The scan did only cover 2/3 of the brain (including temporal and occipital poles, but excluding superior frontal and superior parietal areas) to increase spatial resolution (decreasing voxel size) without decreasing temporal resolution (i.e. increasing scanner TR).

## first level analysis
Each subject folder contains the corresponding SPM.mat and several contrast images and t-maps.
The contrast index are the follows:
- 1 EOI (F-Contrast=
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
(yes some contrasts are redundant).

## Time series
Time Series were extracted for different ROIs (adjusted for the EOI contrast) in all Voxels active at the faces>houses contrast (threshold = ???). The corresponding files have prefix "VOI_".

