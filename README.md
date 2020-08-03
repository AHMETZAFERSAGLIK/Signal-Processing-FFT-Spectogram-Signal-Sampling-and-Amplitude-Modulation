# Signal-Processing-FFT-Spectogram-Signal-Sampling-and-Amplitude-Modulation


In this part of the project you will write the Python code to create Fourier representations 
via 2D FFT for the grayscale images. You can use built-in libraries to calculate 
FFT of images (e.g. np.t.t2). To read and write images, you can benet from the 
following skeleton code which reads an image, rotates it and writes again as a dierent 
le. You will use OpenCV library for this part of the project, but it is not necessary at
1

BLG 354E Signals and Systems for CE 2019/2020 Spring Final Project 
this point to delve into it deeply. 

 Read each of the images. 
 Using 2D-FFT, calculate 2D Fourier representations of these images. 
 Decompose these representations into its magnitudes and phases. Remember, 
phase of each point is just an angle on the complex plane. 
 What kind of operation is needed to recreate the original images from magnitude 
and phase information? Recreate the images and show them. 
 Obtain new images by using one image's phase and other image's magnitude information. 
Using the method given in the previous point, this time you will face 
with two problems: 
{ Very small imaginary values may appear at a level of 10..13s due to numerical 
computation. You may omit imaginary parts. 
{ The recreated image is not between 0-255 now. You should do a max-min 
normalization to remap the image between [0-255]. You can do it with xnew = 
x..min 
max..min  255. 
If everything goes well, you will obtain the images given in Figure 1. 
Explain the eect of using this type of operation on the images. Which eects on the 
images are related with phase information? 
Hint: Be careful about casting since the read images are in unsigned int type (np.uint8). 
However, after doing the operations, you will obtain data from 
oat type. To show the 
images in the correct way, it is useful to recast them to uint8. 

2

Figure 1: Example outputs for Part 1. 
2 The Spectrogram
With the document you will receive two dierent numpy les namely spectrogram.npy 
and phases.npy. These two les are created by analysing a small music le using a 
rectangular lter with size 2000. Step size is also used as 2000. While the spectrogram 
have the magnitude information of the audio as usual, phases.npy has the phase information 
of each windowed area. Instead of using built-in spectrogram functions, you will 
calculate it step by step. 
 Plot the spectrogram in linear scale (Spectrogram A). 
 Reobtain the audio using the given information. 
 Use Hann windows with sizes 500 (Spectrogram B), 2000 (Spectrogram C), 
4000 (Spectrogram D) to obtain new spectrograms. Let step size be equal to 
window size. 
 Compare the four spectrograms. Explain the dierences and the reasons for them 
if any. 

3 Continuous Signal Sampling  
 
 Sample these two signals using 5 dierent sampling frequencies. Plot these sampled 
signals. Among them which are more relatable to the original signals. Show 
undersampled and oversampled examples. Illustrates the phenomenon of aliasing. 
 What are the minimum sampling rates to show these signals? Why? 
 Make Discrete Time Convolution between sampled signals with dierent rates. 
(Please do not use built-in convolution functions, you should write your own convolution 
function.) 

3

BLG 354E Signals and Systems for CE 2019/2020 Spring Final Project 
4 Amplitude Modulation 
In this question, you are expected to implement a Frequency-Division Multiplexing 
(FDM). FDM is used to stack multiple signals on the same channel by allocating the 
dierent frequency bands to each signal. You should build a system which consist of a sinusoidal 
amplitude modulator and sinusoidal demodulator. Please examine the diagram 
given below in detail. Using FDM, we will create a virtual AM radio broadcast system 
which have two channels. Two audio les belonging to _Ilber Ortayl and Emrah Safa 
Gurkan, which are given with the homework le, should be stacked in a single channel 
with amplitude modulator and then reconstructed through the demodulator part of the 
system. For details, please follow the step-by-step description below. 
 Read the sound les and plot their graphics separately in time and frequency 
domain. You can use np.t.t method to obtain discrete Fourier Transform of 
signals and scipy.io.wavle.read method to read sound les. 
 Filter the sound signals with a lowpass lter to obtain bandlimited signals. You 
should decide the bandwidth by examining the signals and their frequencies. Plot 
the ltered signals in the frequency domain. Please brie
y explain why signals 
should be bandlimited before the modulation process. Which problems arise 
if we do not use bandlimited signals in amplitude modulation? You can use 
scipy.signal.butter to design lter. 
NOTE: You don't need to go into the details of the digital Butterworth lter 
design for all lters which are used in this question. You can simply design your 
lters using this sample code and scipy documentation here. 
 Produce two dierent carrier signals to appropriate the bandwidth you decide. 
Write down the frequencies of the carrier signals clearly and brie
y explain why you 
choose these frequencies. In this step, you are expected to try dierent frequencies 
and then observe their results and choose the best combination. 
 Obtain amplitude modulation of the sound signals with carrier signals and stack 
these signals into a single signal. Then, plot the stacked signal in time and frequency 
domain. 
 Implement demodulator part in gure 3 like modulator part. Plot the graphics of 
the results at each step of the diagram. Write the lter parameters of your choice 
clearly for both lters and brie
y describe what you have chosen. Explain why 
these lters are used in the demodulator. 
 Compare reconstructed signals with original ones using graphs in frequency and 
time domain. 
 Write a function that saves the reconstructed audio le of the desired historian 
using your implementations above. You can use scipy.io.wavle.write to save audio 
les. Brie
y interpret the reconstructed sounds and state your observations. 
