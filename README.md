Download Link: https://assignmentchef.com/product/solved-solvedmanipulating-digital-audio
<br>
Set Up You must create a folder project2 in the CS177 folder you created in lab1. You can do this using any Windows machine in the B160 or G066 laboratories. You can do this also by logging into your UNIX CS account and typing the following commands: NOTE: harp-8bit.wav and drumline-8bit.wav should work for all the functions without issuep2lib.py is a library created by us that takes care of all the file output for you. The library contains the write() function that you have to call, with appropriate parameters, to write the modified sound on a file.project2.py is a skeleton file. Write your code there. Note that the skeleton file will compile (when you click IDLE Check Module in the IDLE Run menu).We included two .wav files for testing your program. We will later provide additional files to use.Before you start working, you may want to read this quick tutorial on the wave library you will be using. Introduction In this project, you will be filling the shoes of an audio technician and explore the world of digital sound. You will be learning about what sound is, how it can be represented in the computer, and how to transform and modify the digital representation of sound waves in order to create your own audio files (in .wav format). ObjectivesUse and manipulate arrays/lists with numeric dataPractice different loop structuresLearn about what sound is and how it is represented and managed in the .wav formatBecome familiar with basic principles of digital soundBackground: Sound and Digital Encoding In the physical world, sound exists as fluctuations of pressure in the air around us.These fluctuations are continuous fluctuations over time that take on a continuous range of values, which is referred to as an analog signal. Any periodic analog signal can be decomposed into (and is thus the sum of) a (possibly infinite) number of sinusoidal waves. The simplest pure sound is a single sinusoidal wave, defined by the sine function (see Sine function) Computers, however, cannot easily represent continuous functions because they have a finite amount of memory. Instead, an approximate representation is used, by taking sample values of the continuous function at discrete time intervals. Thus, although we don’t have the original wave, we have samples of where the wave was for a number of points in time. This is referred to as a digital signal. A digital-to-analogue converter can reconstruct the original wave from samples, which can in turn be played on speakers. The rate at which samples are taken is known as the sampling frequency. It is measured in Hertz (Hz), or samples per second. The sample size is the number of digits used in the digital representation of each sample. Higher sampling frequency and higher sample size lead to higher quality sound. An analogue-to-digital converter (ADC) takes an analog signal as an input and produces a digital signal as output. Such a device is used in a microphone. As you speak or play into a microphone, your voice causes a membrane to vibrate. It is recorded how far the membrane is displaced in either direction, many times per second. These samples may be saved easily for playback at a later time. A digital-to-analog converter (DAC) performs a transformation that is the the inverse of the one performed by the ADC. Namely, a DAC takes discrete samples in time and constructs a continuous wave from them. You may find such a device in your sound card or in your CD player. Whenever you listen to a sound on your computer, these discrete samples are converted to a continuous signal that can be fed to your speakers. It is possible to exactly reconstruct an analogue signal from digital samples subject to a few conditions. When recording an analog signal it is important to know the highest frequency that will be captured. This is known as the Nyquist frequency. The Nyquist-Shannon theorem states that it is possible to exactly reconstruct a wave consisting of frequencies up to the Nyquist frequency if the sampling frequency is at least twice as large. The most common sampling frequencies found on audio hardware are currently 11025 Hz, 22050 Hz, and 44100 Hz. Since the average human ear can only hear a maximum frequency of up to 20000 Hz, we should set our sampling rate to at least 40000Hz. Sampling at a higher frequency only results in more samples that can capture sounds that are inaudible to humans. .wav File Format There are many encodings and many standard sampling rates. In the .wav format, stereo files would encode the two channels separately (interleaved). Sample width is the number of bytes. RowRow.wav is a mono file (1 channel) where each sample is one byte wide, and therefore can encode 255 different sample values. A stereo version of this file would have twice as many samples, one for each channel. A frame consists of one sample per channel, thus a frame in RowRow is one byte in size. For a stereo version, at the same sampling density, a frame would be 2 bytes. We will work here with mono files, each frame one byte. PROJECT DESCRIPTION To begin with, create the project2.py Python file (remember to use Python 3.2). Main menu The first thing you have to do is to write the main() function. It must print the menu of the audio functions available to the user: 0 = Quit 1 = Audio File Merge 2 = Adjust Volume 3 = Generate Silence 4 = Copy File Then it should prompt the user for an integer input, each input corresponding to the one of these tasks, and call the appropriate function (see the functions’ description in Part1 – Part3 below), until the user selects the Quit option. The output should appear as follows: Please Select an function 1 = Audio File Merge 2 = Adjust Volume 3 = Generate Silence 4 = Copy File Please enter selection Part 1: Copy File In this function you need to write a function called copyFile() that will ask the user to input the name of a file. That file will then be opened and its contents saved to a new file called output0.wav. Part 2: combine() function You have to write a function called combine() that will combine two audio files. Combining two audio files means appending the content of the second audio file to the content of the first file. In order to do so, you need to open the audio files, read their content into main memory (by assigning it to a variable) and append the content of the second file to the first. Then you need to write the new audio to an output file. This function should be called when the user inputs a 1.The function should initially prompt the user to select 2 audio files of her choosing. Then it should read in all the sample values from the two audio file and store them into variables. The output file called output1.wav should consist of the first file followed directly by the second file; the original files that were given by the user will remain unmodified. Do not forget to close the input files. Note: Due to the difference in frame rates of the different files, you may experience some strange behavior with your output such as distorted sound Part 3: change_volume() For the next task, you should write a function that will modify the volume of a .wav file. You should begin by asking the user for a file and then for the desired change in volume. Any value less than 1 (but greater than 0) will decrease the volume, and any value above 1 will increase the volume; an value of 1 will leave the volume unchanged. The value that the user types in is essentially a factor that you will multiply the sound level or each sample by. Remember, volume is the amplitude of the sound wave, and for mono .wav files, each sample cannot have a value larger than 255 or smaller than 0. Since samples will be read in as a string of bytes, you will have to convert the data to the list type that you can manipulate. Once you are done you will have to convert them back to bytes in order to write them to the output file. The back-conversion is done by the provided function write(name,file1,size,output_list) Again, don’t forget to close the input file. Part 4: silence() For the third part of this project, you will write a function called silence() that will make a portion of an audio file completely silent. You should ask the user to input a file that they wish to modify and then ask them to input 2 points (in seconds) where they would like everything in between to be silent. Just as with part 1, you should not modify the original file, but write the modified version to a new file .wav called output3.wav (already created for you). Remember, that silence is represented by a 0 in the corresponding byte(s). TIPS Here are some tips that you may find useful in doing your project2. First, notice that at the very top of the project2.py the line “import wave”. Wave is a library that allows you to read, write and interact with .wav files. If you take a look at the reference page (see the link below) for a list of functions that you will be using, you will notice that there is no support for reading and writing to the same file, so you will only be reading data from the source files, and writing any changes that you may make to a separate .wav file. In order to write your files, use the write() function provided to you in p2lib.py; note that you should not modify any code in p2lib.py. You should also use theclose() function on a file when you are done using it. Files will not automatically be closed when you exit the program. Think of audio as an array of values that represent the amplitude (the height of the wave) at each sample. There is a useful function called list() which takes in input a sequence and makes an array out of it. For instance, list(‘abc’)returns [‘a’, ‘b’, ‘c’] and list( (1, 2, 3) ) returns [1, 2, 3]. Note that ‘abc’ is a string of characters; (1, 2, 3) is a tuple. Both of them are sequences, since their elements come “one after the other”. Before working with the samples, we need to read them from a .wav file. When reading a .wav file, you need to know how many frames it contains, since the number of frames varies from audio file to audio file. To do that you need to use the getnframes() function of the wave library. Once you know how many frames you must read, then you can effectively read them using the readframes() function of the wave library. Furthermore, the readframes() function returns a string composed of all the frames that constitute the audio file.Note that this function does NOT return a list. Why that? Well, the audio file must contain a number of other data that describe all the characteristics of the audio. The number of frames is one of such data. Other data that are needed to correctly manage the audio are the frame rate, that is the sampling rate, the type of audio (i.e.monophonic or stereo) and a lot more. For the purpose of this project the data you need to know are the number of frames and the frame rate.It is worth noting that the data that describe other data are collectively called meta-data. When dealing with “complex” data, such as audio, meta-data are fundamental; moreover, you can easily understand that there must be an agreement about the meta-data that describe the audio between the “producer” of the audio and the “consumer” of the audio. By “producer” and consumer“ we mean the functions of the program (or libraries) that manage the audio; by “agreement” we mean fixing precise rules about what each-meta data represents, how the meta-data is encode, the relative position of each meta-data. The .wav suffix of the file tells that the file was encoded using the WAV standard. The standard is the “agreement” or common shared rules used to encode the data and the meta-data.From a more practical standpoint, in order to manipulates the values of the audio stream you need to convert the structure returned by readframes() to a list (see the Useful function section about the list() function). You will have to change data types multiple times on data, so be sure you know your data types and how to convert them (Hint: look at the Python standard library page) Here is a link to the wave library for reference: http://docs.python.org/py3k/library/wave.html Link to list of standard library functions: http://docs.python.org/py3k/library/functions.html Useful functions input([prompt]): Prints the prompt on screen and reads in user input. Interprets whatever is input as a string. list([iterable]): Return a list whose items are the same and in the same order as iterable‘s items. iterable may be either a sequence, a container that supports iteration, or an iterator object. If iterable is already a list, a copy is made and returned, similar to iterable[:]. For instance, list(‘abc’) returns [‘a’, ‘b’, ‘c’] and list( (1, 2, 3) ) returns [1, 2, 3]. If no argument is given, returns a new empty list, [ ]. Turnin Instructions You will turn-in your project using the turn-in command you used in lab. Hence, login into your UNIX account on the lore machine, and then launch the following commands: cd cd CS177 NOTE: we assumed that you created a folder CS177 where the initial letters are capital ones. If you used lower case letters (i.e. cs177), be careful to type the folder name using lower case characters. To be sure that the folder project1 is under the folder CS177, type the command: ls and verify that your python.py file is there.