# Music Genre Classifcation

<img src ='/figures/music.jpeg' >


<h2>Purpose</h2>
The purpose of this repo is to classify audio files into genres using feature extraction and spectrograms.

<h2>Data Description</h2>
The Repo is split up into 5 folders 

```
data:
* Final-csvs:
    * data.csv
    * features.csv 
    * genrelist.csv
    * smallgenres.csv
    * smalltracks.csv

Data Prep:
* Creating csv features
* Exploring Datset
* Exploring features for one track
* Getting Dataset
* Saving melspectograms for genres
* Saveing spectrograms for genres

Models:
* Machine Learning Algorithms
* Final Neural Complete
* CNN & Transfer Learning


Figures:
* Contains array of images that are use in the powerpoint pdf

```

<h2> The project follows the CRISP-DM Process <h2>

<h2> Business Understanding </h2>
A music sharing platform wants to increase user experience when uploading audio by making things more automated. They are creating a feature that allows the user to upload their audio file, and the genre of the audio file will be automatically tagged, reducing manual tagging during the upload experience.

<h2> Data Understanding </h2>
The Dataset contained 8000 Audio files, 1000 per genre. 3 files were corrupted which left us with 7997.



<h2> Data Preparation</h2>
The small dataset was extracted from the larger files. This resulted in information about 8000 Audio files, 1000 per genre. 3 files were corrupted which left us with 7997.
A csv file was then created, extracting all the information available from the audio files.
The extracted features were as follows: 

<h4> Spectrograms </h4>
A spectrogram is a visual representation of the spectrum of frequencies of a signal as it varies with time. When applied to an audio signal, spectrograms are sometimes called sonographs, voiceprints, or voicegrams. A spectrogram is usually depicted as a heatmap, i.e., as an image with the intensity shown by varying the colour or brightness. 


<br> Fourier Transform is a function that gets a signal in the time domain as input, and outputs its decomposition into frequencies.<br>


The Short-time Fourier transform (STFT), is a Fourier-related transform used to determine the sinusoidal frequency and phase content of local sections of a signal as it changes over time.

The spectrogram shows the the intensity of frequencies over time. It is simply the squared magnitude of the STFT. The human perception of sound intensity is logarithmic in nature. Therefore, we are often interested in the log amplitude:

<img src ='/figures/Spectrogram.png' >

In 1937, Stevens, Volkmann, and Newmann proposed a unit of pitch such that equal distances in pitch sounded equally distant to the listener. This is called the Mel Scale. We perform a mathematical operation on frequencies to convert them to the mel scale.

A Mel spectrogram is merely a spectrogram that uses frequencies that have been converted to the mel scale.
<img src ='/figures/melspec.png' >

<h4> Chromas </h4>
A chroma vector is a typically a 12-element feature vector indicating how much energy of each pitch class, {C, C#, D, D#, E, …, B}, is present in the signal

- <b>Chroma stft</b>
<img src ='/figures/chromastft.png' >

- <b>Chroma CQT</b>
The constant-Q transform transforms a data series to the frequency domain. Similiar to the mel scale, uses a logarithmically spaced frequency axis
<img src ='/figures/chromacqt.png' >


- <b>Chroma Energy Normalized Statistics (CENS)</b>
Taking statistics over large windows smooths local deviations in tempo, articulation, and musical ornaments such as trills and arpeggiated chords. CENS are best used for tasks such as audio matching and similarity.
<img src ='/figures/CENS.png' >
<h4> Spectral Features </h4>

- <b>Spectral Centroid</b>
The spectral centroid is a measure used in digital signal processing to characterise a spectrum. It indicates where the center of mass of the spectrum is located. Perceptually, it has a robust connection with the impression of brightness of a sound.
<img src ='/figures/spectralcent.png' >

- <b>Spectral Bandwidth</b>
The Spectral Bandwidth is the Wavelength interval in which a radiated spectral quantity is not less than half its maximum value. It is a measure of the extent of the Spectrum.
<img src ='/figures/spectralband.png' >

- <b>Spectral Contrast</b>
The Spectral Contrast is defined as the level difference between peaks and valleys in the spectrum.
<img src ='/figures/spectralcont.png' >

- <b>Spectral Rolloff</b>
The Spectral Rolloff as the frequency below which a specified percentage of the total spectral energy lies.
<img src ='/figures/spectralroll.png' >

- <b>Zero Crossing Rate</b>
The Zero Crossing Rate is the rate of sign-changes along a signal, i.e., the rate at which the signal changes from positive to zero to negative or from negative to zero to positive.
<img src ='/figures/zcr.png' >
- <b>Tonnetz</b>
Various visual representations of the Tonnetz can be used to show traditional harmonic relationships in European classical music.
<img src ='/figures/tonnetz.png' >

- <b>Root Mean Square Energy</b>
The energy of a signal corresponds to the total magnitude of the signal. For audio signals, that roughly corresponds to how loud the signal is.
<img src ='/figures/rmse.png' >

- <b>Mel-Frequency Cepstral Coefficients( MFCCs)</b>
Mel-frequency cepstral coefficients (MFCCs) are coefficients that collectively make up an MFC. They are derived from a type of cepstral representation of the audio clip (a nonlinear "spectrum-of-a-spectrum"). MFCCs of a signal are a small set of 20 features which concisely describe the overall shape of a spectral envelope.
<img src ='/figures/mfcc.png' >

<h2> Modelling </h2>

<h3> Machine Learning </h3>
Using audio features
<h4> Random Forest </h4>
Running a Random Forest model:
Training Accuracy: 51.3%
Testing Accuracy: 42.3%
<img src ='/figures/RF.png' >

<h4> Support Vector Machines </h4>
Running a Support Vector Machine:
Training Accuracy: 61.8%
Testing Accuracy: 50%
Random Chance is 0.12, so model performs approx 4.1 better than random chance
<img src ='/figures/svc.png' >

<h4> XGBoost</h4>
Running an XGBoost model:
Training Accuracy: 59.9%
Testing Accuracy: 47%

<img src ='/figures/xgb.png' >

<h3> Neural Networks </h3>
Model Summary:
<img src ='/figures/modelsummary.png' >
<img src ='/figures/training.png' >
<img src ='/figures/traincm.png' >
<img src ='/figures/testcm.png' >


<h3> Convolutional Neural Networks</h3>

Using Mel-Spectrogram images:
<img src ='/figures/cnn.png' >

<img src ='/figures/cnn2.png' >




<h2>Conclusions</h2>
Neural Network

Model is very poor at identifying Pop tracks
Further investigations:
* Further explore what features of these songs contribute to misclassification
* Misclassified most as Hip-Hop,Rock and Folk

Transfer Learning
Model completely overshoots on Electronic and Rock


<h2>Future Work</h2>
<ol>
<li>Better image quality
    <ul> Run models on fully scaled images for better quality results</ul>
    </li>
<li> More Data
    <ul> More audio files for each genre for better results</ul>
</li>
<li> One vs All
    <ul> Use a one vs all approach to train.
i.e. Pop or not Pop</ul>
</li>
<li> Feature Combinations
    <ul> Explore different combinations of features for optimum results
</ul>
</li>

