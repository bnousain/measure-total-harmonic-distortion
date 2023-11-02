### Measure Total Harmonic Distortion

## Getting started

There are 2 sections to this file:
1) Calibration to find the amplitude of the tone that is uses the full scale of the ADC
2) Measuring the total harmonic distortion at the full scale of the ADC

This script is intended to be run in a Jupyter Notebook.

Python package requirements are listed in requirements.txt, but not in a format that is compatible with pip (yet).

## Overview
This script outputs a series of pure tones from the speaker output and simultaneously records the input of the microphone. 
This requires a computer that has independent ports for speaker and microphone. Many laptops have combined these ports in an attempt to save space.


Inexpensive, external sound adaptors can be used to provide independent ports for the speaker and microphone. Example devices are listed below.

SABRENT USB External Stereo Sound Adapter (AU-MMSA)
https://www.amazon.com/dp/B00IRVQ0F8

SABRENT USB Type C External Stereo Sound Adapter (AU-MMSC)
https://www.amazon.com/dp/B071HJ98Q6

## Configuration of Total Harmonic Distortion (THD) Measurement

fs: Sampling frequency of external sound device. The sound device must be compatible with this sampling rate. 

# experiment settings
numTrials: Number of times to retest the same frequency
expPurpose: Purpose of experiment
deviceUnderTest: Name of Device Under Test (DUT)

# tone generation settings
duration: Length of time, in seconds to generate tone. Longer durations result in longer times to complete the characterization
toneAmplitude: Amplitude of the tone to be output from audio jack. This value should be the value that results in using the full range of the ADC. This value is calculation by the calibration script.
minFreqToTest: Minimum frequency of tone to generate (Hz)
maxFreqToTest = Maximum frequency of tone to generate (Hz)
freqSpacing = Spacing between consecutive frequencies (Hz)

# analysis settings
fundFreqNotchWidthFract: Width of the brick wall notch filter in frequency domain when measuring distortion expressed as a fraction of the fundamental frequency
fundFreqSearchWidthFract: Width of the range to search for max amplitude relative to fundamental frequency
startBuffer = 0.25: Number of seconds from beginning of recorded file to ignore
endBuffer = 0.25: Number of seconds from end of recorded file to ignore
saturationThreshold: Max allowed value of the samples before declaring saturated input
numSampsAtSatToAllow: Number of samples to allow above saturation threshold
underDriveThreshold: If max value of signal is not above this then signal might not be present

## Execution
THD.ipynb is the script that contains the calibration and measurement sections. This script will save itself each 
time it is run to ensure the current configuration are archived to the Git repo in order to archive the code state 
for every data collection.
