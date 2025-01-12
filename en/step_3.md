## Writing your program and resources to help

This section will help you get started with writing your program, and provide links to other project guides that will help you develop some of the coding skills you may need. You can choose which project guides you want to look at depending on which of the sensors and/or camera you are going to use in your program. At this point, you should have already spent some time with your team and your team mentor to plan your program, and have decided what data you are going to collect to make your calculations.

We recommend that you start writing your program in small steps, and that you do not try to do everything at once. 

--- task ---

To keep everything organised, create a folder to store all your project files. For the name of the folder, you may wish to use your team name.

--- /task --- 

### The main.py file

Every submission must include a file named `main.py`. This is the file from which your program will run, and which will be tested by Astro Pi Mission Control. When you run the finished program, it should do everything you need to estimate the speed of the ISS. Start by making a file for your main program, and add in the code that you get working as you go along.

--- task ---

Create a new file in Thonny and **Save as** `main.py` in your project folder.

--- /task --- 

### Test your program with the Astro Pi Replay Tool

The Astro Pi Replay Tool acts as a kind of simulator you can use on Earth that will make your program act as if it is running on an Astro Pi on board the ISS. It allows you to test your code before it goes to space without needing to have a Raspberry Pi, camera, or Sense HAT. The simulation is not perfect, however, and will only produce photos and sensor data from within its own data set, but it should still allow you to test that your program would work when running on board the ISS.

There is an online version and an offline version, available as a Thonny plug-in, for you to test your program. We recommend you use the online version of the tool. 

--- collapse --- 
---
title: Accessing the Astro Pi Replay Tool online 
---
The easiest way to test if your program will work on the ISS is to upload your main.py file to the online [Astro Pi Replay Tool](https://missions.astro-pi.org/msl/replay-tool). 

To upload your program simply, open the link and either drag and drop, or select, your main.py file and click run. The Replay tool will run your program in full, and show you the images and data you have captured, along with any files that your program outputs. 

**Make sure your program has an output with your final speed estimate in kms (kilometres per second).**
--- /collapse --- 


--- collapse ---
---
title: Installing Astro Pi Replay Tool on Raspberry Pi Bookworm
---
If you are on Raspberry Pi OS Bookworm, please follow the instructions on how to configure Thonny to use a virtual environment on the [raspberrypi website](https://www.raspberrypi.com/documentation/computers/os.html#using-the-thonny-editor) before proceeding with the instructions below.

To install the Astro Pi Replay tool, open Thonny, then click on **Tools > Manage plug-ins...**, and search for `thonny-astro-pi-replay`. Select the correct plug-in, then press **Install**.

![Screenshot of the plug-in manager in Thonny, showing search results for the "thonny-astro-pi-replay" library.](images/install_replay_1.png)
 
![Screenshot of the plug-in manager in Thonny, showing the "thonny-astro-pi-replay" library and the 'Install' button.](images/install_replay_2.png)

Then, click on **Tools > Manage packages...**, and search for `astro-pi-replay`. Select the correct package, then press **Install**.

![Screenshot of the package manager in Thonny, showing search results for the "astro-pi-replay" library.](images/install_replay_3.png)

![Screenshot of the package manager in Thonny, showing the "astro-pi-replay" library and the 'Install' button.](images/install_replay_4.png) 

If you have taken part in Mission Space Lab before and have already downloaded the Astro Pi Replay tool, you should re-install the `astro-pi-replay` library to make sure you have the latest version. To do this, remove the `~/.astro_pi_replay` directory in your home folder (e.g. using the command `rm -rf ~/.astro_pi_replay` in a Terminal window) and then follow the instructions above, as if you had not installed `astro-pi-replay` before.

**You will need to close and restart Thonny for the installation to complete.**

<p style="border-left: solid; border-width:10px; border-color: #0faeb0; background-color: aliceblue; padding: 10px;">

The Astro Pi Replay tool works by replaying a set of old pictures taken on the ISS. When your code goes to take a picture, instead of accessing some camera hardware, the library selects a picture to replay and acts as if it has just been captured 'live'.

![Screenshot of the 'Run' menu in Thonny, with 'Astro-Pi-Replay' highlighted in the menu.](images/use_replay.png){: width="50%"}

<br>

**How to use the Astro Pi Replay plug-in**
<br>
To run your code using the Astro Pi Replay plug-in, do **not** press the green **Run** button. Instead, open the **Run** menu, then click on **Astro-Pi-Replay**. This will run your code as if it was running on Astro Pi hardware.
--- /collapse ---


**Note:** Although all of the functions of the `picamera-zero` library are available, many of the `picamera-zero` settings and parameters that would normally result in a different picture being captured are silently ignored when the code is executed using Astro Pi Replay. Additionally, most attributes on the `Camera` object are ignored. For example, setting the resolution attribute to anything other than `(4056,3040)` has no effect when simulated on Astro Pi Replay, but would change the resolution when run on an Astro Pi in space.
</p>


### Calculating with historical data

You may wish to start by learning how to write a program that estimates the speed of the ISS using photos with our [Calculate the speed of the ISS using photos](https://projects.raspberrypi.org/en/projects/astropi-iss-speed/0) project guide. Once you have written a program, you can try it out using different images or data sets to improve the accuracy of your estimate. Here are some examples of images and data you can use:


- [Astro Pi Mission Space Lab 2022/23 photos](https://www.flickr.com/photos/raspberrypi/collections/72157722152451877/)
- [Astro Pi Mission Space Lab 2022/23 data](https://docs.google.com/spreadsheets/d/1RjPEp2IHVB6For65wuUQdWntsg1H5sHWpYUtLzK9LCM/edit?usp=sharing)

<p style="border-left: solid; border-width:10px; border-color: #0faeb0; background-color: aliceblue; padding: 10px;">
Don't forget that you will only be able to use the visual light camera on the ISS this year.
</p>

### Simulate running your program in real time

You may prefer to get started by using the `sense_hat` and `picamera-zero` libraries and simulating running your program in real time. To simulate reading data from the Sense HAT and capturing photos from the camera, you will use the Astro Pi Replay tool online or with Thonny. 

### Taking measurements with the Sense HAT 

In order to calculate the speed of the ISS, you may wish to gather data from the sensors on the Sense HAT. Check out our [Getting started with the Sense HAT](https://projects.raspberrypi.org/en/projects/getting-started-with-the-sense-hat) project guide to learn how to do this.

### Taking photos with the camera

You may also wish to use the camera to take photos of the Earth to use in your program. You can use our [Getting started with the Camera Module](https://rpf.io/gswpicamera) project guide to learn how to do this. However, if you do not have a Raspberry Pi and High Quality Camera to test your code on, you can still run the same code using the Astro Pi Replay Tool.

Here is an example of a simple program to test the Astro Pi Replay plug-in, if you are using the offline version in Thonny: 
```Python
# Import the Camera class from the picamera-zero module
from picamzero import Camera

# Create an instance of the Camera class
cam = Camera()

# Capture an image
cam.take_photo("image1.jpg")
```

This will simulate taking a picture on the ISS and save it in a file called `image1.jpg`. If you open this file, you should see the exact photo below. 

![Photo of clouds above land.](images/image1.jpg)

The `picamera-zero` library supports a variety of features and camera settings. You can see some examples by going to the ['Recipes' page](https://raspberrypifoundation.github.io/picamera-zero/recipes/) on the picamera-zero website, but be mindful that if your code is run on the ISS, it will be taking pictures of a variety of weather conditions with a range of clouds, landscapes, and lighting. However, your program is always guaranteed to be run in daylight.

While all features of the `picamera-zero` library will be available on the Astro Pi in space, not all can be simulated by the Astro Pi Replay Tool.

### Capturing sequences

Using `picamzero` it is very simple to take a sequence of pictures by calling the `capture_sequence` function. The example below takes three pictures in succession, with a 3 second gap between each one.

Create a new file called `camera-sequence.py`, and in it, type the following lines:

```Python
# Import the Camera class from the picamzero (picamera-zero) module
from picamzero import Camera

# Create an instance of the Camera class
cam = Camera()

cam.capture_sequence("sequence", num_images=3, interval=3)
```
Run this code using [Astro Pi Replay online](https://rpf.io/astro-pi-replay-online)), or with the Thonny plug-in by clicking on **Run > Astro-Pi-Replay**.

### Numbering plans for images and files

When dealing with lots of files of the same type, it is a good idea to follow a naming convention. In the example above, we use an obvious sequence number — `image1.png`, `image2.png`, etc. — to keep our files organised.

If you need more help with using the camera, check out the ['Take still pictures with Python code' step](https://projects.raspberrypi.org/en/projects/getting-started-with-picamera/5) in our 'Getting started with the Camera Module' project guide.

--- task --- 

Update your `main.py` file to capture images or Sense HAT data in real time.

--- /task --- 

### Finding the location of the ISS

You will be able to download up to 42 pictures that you take on the ISS. It can be nice to know where exactly an image was taken, and this is something you can do easily with the `astro_pi_orbit` and `exif` libraries available on the Astro Pis.

The following is an example of a program that will, when run using the Astro Pi Replay Tool, create a new image called `gps_image1.jpg`. The `picamzero` library will have set the Exif metadata for the image to include the current latitude and longitude of the ISS.

```Python
from astro_pi_orbit import ISS
from picamzero import Camera

iss = ISS()

def get_gps_coordinates(iss):
    """
    Returns a tuple of latitude and longitude coordinates expressed
    in signed degrees minutes seconds.
    """
    point = iss.coordinates()
    return (point.latitude.signed_dms(), point.longitude.signed_dms())

cam = Camera()
cam.take_photo("gps_image1.jpg", gps_coordinates=get_gps_coordinates(iss))
```

You will need to use the Astro Pi Replay tool to run this snippet.

<p style="border-left: solid; border-width:10px; border-color: #0faeb0; background-color: aliceblue; padding: 10px;">
  
Note that the latitude and longitude are `Angle` objects while the elevation is a `Distance`. The Skyfield documentation describes [how to switch between different angle representations](https://rhodesmill.org/skyfield/api-units.html#skyfield.units.Angle) and [how to express distance in different units](https://rhodesmill.org/skyfield/api-units.html#skyfield.units.Distance).

</p>

### Machine learning with the Coral accelerator

If you have access to a Coral machine learning accelerator, check out our [Image classification with Google Coral](https://projects.raspberrypi.org/en/projects/image-id-coral/2) project guide. You will walk through the process of training a machine learning model to classify images, and experience using the TensorFlow Lite library. You can then use a similar approach to classify images played back when you run your program using the Astro Pi Replay Tool, or on the ISS.

Once you have completed this project, you may want to look at the [Coral examples page](https://coral.ai/examples/) and [this GitHub page](https://github.com/robmarkcole/satellite-image-deep-learning#datasets) for some inspiration on how to apply machine learning techniques to your own experiment. 

### Writing your result file 

For your submission to pass testing by Astro Pi Mission Control, your program needs to write a file called `result.txt` that contains your estimate for the speed of the ISS. This file must be in text file format (`.txt`), and will contain your estimate to up to five significant figures. Please do not include any other data in this file, including units e.g. `km/s`.

```Python
7.1235
```
*Example result.txt for an average speed estimate.*

The following is an example of a program that will write a .txt file called `result.txt` with an estimated speed value in kilometres per second (km/s) to 5 significant figures. You will have to adapt this code to suit your particular program.

```Python
estimate_kmps = 7.1234567890  # Replace with your estimate

# Format the estimate_kmps to have a precision 
# of 5 significant figures
estimate_kmps_formatted = "{:.4f}".format(estimate_kmps)

# Create a string to write to the file
output_string = estimate_kmps_formatted

# Write to the file
file_path = "result.txt"  # Replace with your desired file path
with open(file_path, 'w') as file:
    file.write(output_string)

print("Data written to", file_path)
```
--- task --- 

Update your `main.py` file so that it writes a file called `result.txt` when it is executed.

--- /task --- 

<p style="border-left: solid; border-width:10px; border-color: #0faeb0; background-color: aliceblue; padding: 10px;">

Make sure to check the [Mission Space Lab rulebook](https://astro-pi.org/mission-space-lab/rulebook) for rules on files and file names.

</p>
