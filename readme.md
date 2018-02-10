# HTML5, Javascript, CSS
In the folders above is my coursework from a class I took on [Coursera](https://www.coursera.org) via The Hong Kong University of Science and Technology. It was a basic course that exposed me to the different elements of creating web pages. It also enabled me to create a HTML5 app to play video at work for testing. I'll give a quick high-level overview here since I can't share the code.

## Overview
The purpose of my test app was five-fold.
  - to display the video of a given channel tuned via QAM or IP
  - to have the capability of play/pause, volume up/down/mute
  - to present stream info and timing when each [HTML5 Audio/Video](https://www.w3schools.com/tags/ref_av_dom.asp) and specific platform events occurred such as state changes (opening, playing, closing, idle), A/V decoder lock, front-end lock, A/V pid availability (PMT), channel number and url
  - to dump the timings in a log
  - to automate ChUp tuning test to capture overall metrics to be parsed by another tool I wrote in Python that provides a summary of the events broken down individually with avg/min/max/std dev.
  
## High-level details how it was done

### HTML5
I created labels and assigned each a class name and class id. The labels were split into two classes.
  - static: These labels were never going to change because it was a name of an HTML5 tag
  - dynamic: These labels will get updated periodically as needed which stores the time that event occurred

To keep the code more flexible, I used the tag name as the class id and frame sets to organize the information visually. On loading of the page, I added event listeners for the HTML5 tags using tag and an anonymized function to a generic update function. When there was an update for a given tag, I would search events I'm tracking based on the "dynamic" class name and specific class id and update the corresponding label. Using a timer, the values would be updated unless a tune is on progress. If that was the case, the timer would restart updating after 10s.

### CSS
The CSS was minimal. The frameset, static and dynamic labels contained their color value and positions and the video contained the position in the top left quarter of the screen.

### Javascript
I used javascript to navigate the DOM to update the "dynamic" labels.

### Other cool stuff (by calling APIs in the platform)
* On loading of the app, retrieved the channel map
* Each time a tune occurs, displayed the channel number on the front panel for 6 seconds and then go back to display the time
* The app runs on both the server and client set-tops

## What I didn't get a chance to complete
Well afterall it was a test app for my own purposes (though I did share it with my coworkers). But if I had to revisit it there are a few things I may try down the road. Things like adding DVR recording and playback capability as well as a configuration page to replace the hard-coded values like remote control key codes and server IP address would be awesome.

## Summary
Overall, this was a fun little side project and I got to reinforce what I learned in the course.
