# Phonocardiogram Classification - Exploring Machine Learning
Brainstation 2022 Spring Capstone Project

Author: Jake Dumbauld
Contact: jacobmilodumbauld@gmail.com
Date: 4/2/2022

INTRODUCTION
------------

For my first machine learning project I chose to participate in the Physionet 2022 Challenge for Computing in Cardiology. The initial goal of the project was to make a neural network that could classify phonocardiograms. The goal eventually evolved to evaluating different types of models and networks with and without the inclusion of patient information. 

Data Sourced from : https://moody-challenge.physionet.org/2022/

REQUIREMENTS
------------
Please create a conda environment using the enclosed yml. Also, please run the enclosed bash script in a dir of your choosing to create the necessary directories.

SUBMISSION CONTENT
------------------
Juptyer Notebooks: There are 6 primary notebooks and 9 secondary noteboooks enclosed. The primary notebooks are as follows:

- '1 - Basic Librosa': This notebook contains exploration of the librosa library, as well as a few lines of code that generate visualizations of the data that will be used in upcoming presentations. 
- '2 - Importing Signal Data': This notebook contains code that uses the librosa library to generate arrays of amplitude data from each of the enclosed .wav files in the downloaded dataset. Two primary arrays were generated, one using a 1K sampling rate, and another using a 4K sampling rate. These were combined with the patient information enclosed in the dataset to make the final arrays. 
- '3 - Isolating Signals & Target Variable for Simple Modelling': In this file I binarized the target variable, presence of a murmur, and trimmed and padded the 4k signal data so that they were all 12 second clips so that they could be used in simple modelling approaches. 
- '4 - Simple Modelling': In this notebook I tried to use Linear Regression, SVM, and KNN to generate predictions on the data set. This, predictably, did not pan out and my model performance was poor across the board. KNN did yield the best results out of the box, but I was unable to squeeze any additional performance out of it through a Grid Search. 
- '5 - Constructing Data Sets for Neural Networks': In this notebook I selected features from the patient info in the data set, and converted the categorical/text variables into numeric variables. I then generated Mel Frequency Cepstral Coefficients (MFCCs) for the signal data. Using this, I created four output arrays to be used in modelling: MFCCs with and without patient info, and signal data with and without patient info.

The 9 seconday notebooks are enclosed in the directory '6 - Model Search':

- Each of these notebooks contains similar code that uses kerastune to search a constrained space of potential model structures with constrained randomness, and then saves the best model to be analyzed in the final notebook. Model types as well as the data they were trained on are listed below.
	- 0 - 4k signal data, no patient, simple sequential
	- 1 - 1k signal data, no patient, simple sequential
	- 2 - 1k signal data, with patient, simple sequential
	- 3 - 4k MFCC, no patient, simple sequential
	- 4 - 4k MFCC, with patient, simple sequential
	- 5 - 4k MFCC, no patient, convolutional
	- 6 - 4K MFCC, with patient, convolutional
	- 7 - 1K signal, no patient, LSTM
	- 8 - 1K signal, with patient, LSTM
Each of the models was then trained on the data and saved. 

To save you the VERY long runtime of these notebooks, the saved models can be downloaded at the following link: https://drive.google.com/drive/folders/1FVCCA5WK00BlfszISuJY7lcnMFNEotEH?usp=sharing.

Returning to the primary notebooks: 

- '7 - Comparing and Evaluating Networks': This notebook trained each of the best models (not including LSTM for reasons discussed in the technical report) 30 times in an environment with unconstrained randomness and gathered information about their performance to generate visuals and insights into each model.


Technical Report:

The enclosed pdf is a technical report containing findings and my own thoughts on the project as a whole. To get a more complete understanding of the decisions made throughout the project, I encourage you to read it!