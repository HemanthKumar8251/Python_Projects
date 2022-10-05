Python Project | Voice Recorder Using Python

Introduction:

A voice recorder is found in every smartphone and computer today. It is an application that is used to record sound and save it in a specific file format, which can be listened to and transferred to another device. If you want to know how to make a voice recorder using python, this article is for you. In this article, I will walk you through how to make a voice recorder using Python.

Project Prerequisites:

To create a voice recorder using the Python programming language, you need to use the sounddevice library in Python. The sounddevice library will help you to record your voice, but to save your voice in a specific file format, you need to use the SciPy library in Python
If you have never used this library before, you can know about it here - 
https://python-sounddevice.readthedocs.io/
To know about the SciPy module refer this link - https://scipy.org/

Getting Started:

Installing the required package: 

You can easily install it by using the pip command mentioned below:
pip install sounddevice.

We must also install the SciPy module and this can be done using the command: pip install SciPy.

After installing the required modules, we will create a folder named “VOICE_RECORDER”.

After creating the folder create python file with the name “voicerecoder.py”.

Code Implementation: 

First, we import the modules that we will be using for this project.
We import the sounddevice module using the import keyword.
Coming to the SciPy package we will import the write method using both the form and import keywords.
import sounddevice
from scipy.io.wavfile import write

After that, we will take input the number of seconds we want to record the voice.
time = int(input("Enter time limit for recording in seconds : "))

We will also take input the name of the file that we want the voice to be saved along with the extention.
name = input("Enter the name that you want the file to be saved with the extension .wav")

Now, we will define a function to record the voice and save the file which takes the parameters seconds and file which are the time we want to record and the file name that we want to save the voice with respectively.
def voice_recorder(seconds, file):

In the first line of the function we’ll print the prompt “Recording Started…” just to know that the recording has started.
    print("Recording Started…")

We’ll use the sounddeive.rec() method to record the audio and the sounddevice.wait() method to record for the given time.
recording = sounddevice.rec((seconds * 44100), samplerate= 44100, channels=2)
    sounddevice.wait()

We’ll use the write() method that we imported form the SciPy package to save the file in the same folder as the project.
    write(file, 44100, recording)

In the last line of the function we’ll print the prompt “Recording Finished” just to know that the recording has stopped.
voice_recorder(time,name)

At last we will call the function with the required parameters.
voice_recorder(time,name)

That’s all for the code…
Source Code:
import sounddevice
from scipy.io.wavfile import write

time = int(input("Enter time limit for recording in seconds : "))
name = input("Enter the name that you want the file to be saved with the extension .wav")

def voice_recorder(seconds, file):
    print("Recording Started…")
    recording = sounddevice.rec((seconds * 44100), samplerate= 44100, channels=2)
    sounddevice.wait()
    write(file, 44100, recording)
    print("Recording Finished")

voice_recorder(time,name)

Now run the code and check if its working or not:
First, we have to enter the time in seconds. 
After that, we’ll enter the name we want the file to be saved along with its extension.

We can see the file in the same folder with the name that we entered.

Congratulations you now know how to record voice using python.