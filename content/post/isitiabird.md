---
title: "Convolutional Neural Network Bird Detector"
date: 2017-06-10
hero: "/images/isitabird.png"
---

~~Now live at [isitabird.mckeogh.tech](https://isitabird.mckeogh.tech) EDIT: Also now written entirely in Go!~~

It’s been done many times already, but I needed a project to distract from my looming exam results. Like many others, I saw xkcd No. 1425 as a challenge, and in a few hours I had a working bird classifier, written in Python. New code available on [GitHub](https://github.com/fmckeogh/isitabird-go).

There are many much better written articles online describing how it works, but essentially small mathematical functions, like neurones in a brain, make up networks that will take an input, apply those functions to it and produce an output. You can create layers of networks to do different things and chain them in different ways to manipulate the data. Then you get your network and teach it to decide whether a picture is “bird” or “not bird”.

Pedro Domingo explains it best when he describes machine learning as instead of inputting data and an algorithm to a computer and then receiving an answer, you input data and an answer and receive an algorithm.

One would assume that teaching a machine to teach itself to recognise images would be the difficult part and allowing others to use it would be easy, however you would be mistaken. I spent days attempting to build an Angular front-end (a futile attempt to use “modern” web development practices), but I couldn’t even find a reliable mechanism to upload files. The solution was Flask, which allowed me to quickly build a nice-ish looking page, that runs a bash script on uploading a file, that runs the Python application that uses the trained model to output two values, one for the amount of “bird” and another for the amount of “not bird”. The page then takes these two, converts them to percentages and gives the user their answer.

The usefulness of such a website is still quite unclear to me, however I enjoyed it nonetheless.

On an unrelated note, I am looking for investors to help me take a groundbreaking new product to market. The IPO will be in the neighbourhood of \$1.5B, so I’m only considering serious investment.
