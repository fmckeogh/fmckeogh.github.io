+++
title = "RGB Motion Reactive Bluetooth Snowboard"
description = ""
date = 2017-01-06
+++

<p align="center">
<iframe src='https://gfycat.com/ifr/OblongEcstaticBoar' frameborder='0' scrolling='no' height="530" allowfullscreen></iframe>
</p>
The weekend before we left on a winter holiday, I saw a bluetooth module and an Pro Mini on a breadboard and had an idea. What if I could control the lighting on a snowboard with my phone?

4 hours later, an LED strip and 5V regulator ordered, I set out to create a lighting system that I could install onto my board. Since I would be renting one and I couldn’t take any tools on the plane I had to plan carefully. I decided to use double sided foam tape to secure everything to the board, and to have two strips of LEDs with power and data connected at the centre, allowing for a short run between the controller and the lights.

First step was to desolder the 90 degree header from the HC-05 module and resolder a straight row.

<p align="center">
<img src="VMplK3d.jpg" style="width:50%;"/>
</p>

With that done, I assembled the breadboard. Ideally, designing PCB wouldn’t have be to much trouble but I was incredibly short on time and being able to change connectors without a soldering iron would help.

<p align="center">
<img src="9HFmjVU.jpg" style="width:50%;"/>
</p>

<p align="center">
<img src="VYnqzj5.jpg" style="width:50%;"/>
</p>

On Tuesday the switching regulator arrived. I needed a waterproof and sturdy container for my project, so a lunch box was the closest I could get. I used hot glue for the breadboard and regulator, velcro for the battery. I soldered an XT-60 connector straight to the regulator and 2 wires for 5v power to the microcontroller, IMU and Bluetooth. I left the screw terminals on as I thought that would be the best compromise between strength and ease of use. Unfortunately I had overestimated how easy it is to find a screwdriver, and tape was used to hold wire in the terminals on the board. Oh well.

<p align="center">
<img src="1ZtMUN1.jpg" style="width:100%;"/>
</p>

The next step was writing the Android app. So I did that, giving basic controls like brightness, mode and other stuff like a fun police coloured lighting.

In the airport there was no hassle, nobody seemed to mind or care about the mess of electronics and duct tape in my carry on luggage. Once I got my board, I dried it off and began applying the tape to the electronics first then attaching to the board. The tape held really well, even in the cold and the wet. Here is the video from the first run with the LEDs.

I had an issue with the cover of the lunchbox, in that it fell off and immediately the box was filled with snow. Luckily everything has survived and seemed largely unaffected. At one point the LED animations seemed remarkably slow, I guess due to the cold having an affect on the crystal controlling the clock speed of the Atmega328. This being the first day I did not bring my phone and set the LEDs to just cycle through the preset FastLED modes. I forgot to set the lights to full brightness and since I was testing in the morning not afternoon they don’t look too impressive.

<p align="center">
<iframe width="640" height="360" frameborder="0"
src="https://www.youtube.com/embed/wZEzDv0ntns">
</iframe>
</p>

Upon arriving home from the slopes, I saw the positive power terminal on the LEDs was pulling off, not due to a cold solder joint before any accusations are thrown, but due to the delicate traces on the strip pulling off. Without my soldering iron these could not be repaired and so the LEDs never saw a second day snowboarding.

Overall it was a very fun project and gave me a good refresher in my Java to write the Android app.
