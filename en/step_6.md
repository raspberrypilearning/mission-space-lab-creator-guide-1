## Testing your program

You should now test it using `Astro Pi Replay`. Doing this gives your entry the best chance of success and confidence that it will work aboard the ISS. When Astro Pi Mission Control receives your program, it will be tested and evaluated using Astro Pi Replay, and if it succeeds, on an actual Astro Pi. Hundreds of teams submit programs to the challenge each year and, unfortunately, there is not enough time to check for mistakes or debug complex code errors. If your program has errors when we test it, your program will not be eligible to run on the ISS.

If you’ve been following this guide from the start, you should have Astro Pi Replay already installed. The installation instructions can be found earlier in this guide and in the Astro Pi Replay documentation.

To test your program and simulate it running aboard the ISS, run your `main.py` code through the Astro-Pi-Replay plugin by clicking **Run > Astro-Pi-Replay**.

Your code should run for less than 10 minutes and then stop.

When it’s finished, double check that it created a `result.txt` file in your project folder with a valid structure. Additionally, observe any other output files created by your project. Did your saved files exceed the 250MB limit, or include file types that are not allowed in the rules? Finally, check your logs for any errors.

If you see any errors, or the program doesn’t do what you expected it to, you’ll need to address this before you submit your code to ensure that you have a chance of achieving ‘flight status’. You can repeatedly call `Astro-Pi-Replay` to rerun your experiment as many times as needed until you are confident that your program works.

--- task ---

Test your program with `Astro-Pi-Replay` and check the output for any problems or unexpected behaviour.

--- /task ---

### Program Checklist

Your program will also be analysed to make sure that it adheres to the guidelines. Take the time now to read them again and re-review your program to ensure it fits the bill.

--- task ---

Check your program against the [Mission Space Lab Program Checklist](https://astro-pi.org/mission-space-lab/guidelines/program-checklist).

--- /task ---

Many Mission Space Lab teams have not had their programs run on the ISS due to some common mistakes or errors in their programs. Below you will find a list of common mistakes with descriptions of why they affect the programs running on the ISS. 

### Common mistakes 

--- collapse ---
---
title: "[Opening and closing the camera repeatedly]"
---

If you close and re-open the camera multiple times, for example in a loop, you are likely to make the Raspberry Pi run out of memory and be rejected by Mission Control.

--- /collapse ---

--- collapse ---
---
title: "[Not using full resolution images]"
---

Beware that the ground sampling distance, or GSD, can change with the final resolution of the image.

The value used in the [Calculate the speed of the ISS with photos](https://projects.raspberrypi.org/en/projects/astropi-iss-speed/0) project is valid for images in full resolution `(4056x3040)` but not necessarily for smaller resolutions. For this reason, we recommend that you capture full resolution images.

--- /collapse ---

--- collapse ---
---
title: "[Storing more than 42 images]"
---

Your program is not allowed to retain more than 42 images at the end of the 10 minutes - though it can store more than that while it is running. 

--- /collapse ---

--- collapse ---
---
title: "[User input]"
---

Your program cannot rely on interaction with an astronaut to work.

--- /collapse ---

--- collapse ---
---
title: "[Using the LED matrix]"
---

Your program is not allowed to use the LED matrix.

--- /collapse ---

--- collapse ---
---
title: "[Poor documentation]"
---

When you’ve created a useful piece of software and you want to share it with other people, a crucial step is creating documentation that helps people understand what the program does, how it works, and how they can use it. Make sure your program contains comments and the method used to determine the speed of the ISS is well explained

[This project](https://projects.raspberrypi.org/en/projects/documenting-your-code/) shows you the recommended way to add useful comments to your program.

Note: Any attempt to hide, or make it difficult to understand, what a piece of code is doing may result in disqualification. And of course, there should be no bad language or rudeness in your code.

--- /collapse ---

--- collapse ---
---
title: "[Overfitting to the replayed data]"
---

Your code must be responsive to the images and sensor data on the ISS and not rely on specific landmarks or geographic areas shown in the sequence(s) used in Astro Pi Replay.

--- /collapse ---

--- collapse ---
---
title: "[Use of absolute file paths]"
---

Make sure that you don’t use any specific paths for your data files. Use the __file__ variable.

--- /collapse ---

--- collapse ---
---
title: "[Not saving data immediately]"
---

Make sure that any experimental data is written to a file as soon as it is recorded. Avoid saving data to an internal list or dictionary as you go along and then writing it all to a file at the end of the experiment, because if your experiment ends abruptly due to an error or exceeding the 10 minute time limit, you won’t get any data.

--- /collapse ---

--- collapse ---
---
title: "[Running out of space]"
---

You are allowed to produce up to 250MB of data. Remember that the size of an image file will depend not only on the resolution, but also on how much detail is in the picture: a photo of a blank white wall will be smaller than a photo of a landscape. Using Astro Pi Replay will give you a good idea of how many pictures you will be able to take.

--- /collapse ---

--- collapse ---
---
title: "[Forgetting to call your function]"
--- 

We’ve seen cases where teams have written a function only to forget to call it in their `main.py` — oops!

--- /collapse ---

--- collapse ---
---
title: "[Saving into directories that don't exist]"
--- 

A number of teams want to organise their data into directories such as data, images, etc. This in and of itself is a really good thing, but it’s easy to forget to make these directories before writing to them.

--- /collapse ---

--- collapse ---
---
title: "[Networking]"
--- 

For security reasons, your program is not allowed to access the network on the ISS. It should not attempt to open a socket, access the internet, or make a network connection of any kind. This includes local network connections back to the Astro Pi itself. As part of testing your program, you should disable your network connection to make sure that your program runs successfully without an internet connection.

--- /collapse ---

--- collapse ---
---
title: "[Trying to run another program]"
--- 

In addition to not being able to use any networking, your program is not allowed to run another program or any command that you would normally type into the terminal window of the Raspberry Pi, such as `vcgencmd`.

--- /collapse ---

--- collapse ---
---
title: "[Multiple threads]"
--- 

If you need to do more than one thing at a time, you can use a multithreaded process. There are a number of Python libraries that allow this type of multitasking to be included in your code. However, to do this on the Astro Pis, you’re only permitted to use the threading library.

Only use the threading library if absolutely necessary. Managing threads can be tricky, and as your program will be run as part of a sequence of many other programs, we need to make sure that the previous one has ended smoothly before starting the next. Rogue threads can behave in an unexpected manner and take up too much of the system resources. If you do use threads in your code, you should make sure that they are all managed carefully and closed cleanly at the end of your program. You should additionally make sure that comments in your code clearly explain how this is achieved.

--- /collapse ---

--- collapse ---
---
title: "[Setting the program execution time too short]"
--- 

Some teams set their program execution time to a small value (e.g. 1 minute) for testing and then forget to switch it back to an appropriate value. Make sure to use as much of your allocated time slot as possible.

--- /collapse ---

--- task --- 

Review your program again. Can you spot any of the common mistakes in your program?

--- /task ---