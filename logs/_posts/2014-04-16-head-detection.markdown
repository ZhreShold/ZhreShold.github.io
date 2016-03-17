---
layout:     post
title:      "Realtime head detection using Adaboost and haar features"
subtitle:   "Extremely fast implementation with minimum dependencies"
date:       2014-04-16 19:15:23
author:     "Joshua Z. Zhang"
header-img: "img/post-bg-05.jpg"
disqus:		yes
---

A fast, embedded system friendly head detector, implemented with Haar-feature and Adaboost classifier.

## Algorithm
This project mainly follows the idea of Viola-Jones face detector. The head detector can be even faster than face detector due to its relatively simpler *features*. We rewrite the Adaboost module to eliminate external dependencies in this project.

The detector runs at around 100 FPS, depending on the computation resources. And the speed could be further improved by introducing cascade as was done in OpenCV.

## Demo

<iframe width="420" height="315" src="https://www.youtube.com/embed/PRbr9-_xLzs" frameborder="0" allowfullscreen></iframe>

We only used several hundreds of training images in this demo and it took about 2 hours for training, the more data we got, the better detector we got. However, it requires more human labor to get labeled images.
