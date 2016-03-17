---
layout:     post
title:      "Animal segmentation and detection in wild"
subtitle:   "Object segmentation and detection in cluttered scenes"
date:       2014-11-10 15:16:40
author:     "Joshua Z. Zhang"
header-img: "img/post-bg-02.jpg"
disqus:		no
---

We consider video object cut as an ensemble of framelevel background-foreground object classifiers which fuses information across frames and refine their segmentation results in a collaborative and iterative manner.

Our approach addresses the challenging issues of modeling of background with dynamic textures and segmentation of foreground objects from cluttered scenes. We construct patch-level bagof-words background models to effectively capture the background motion and texture dynamics. We propose a foreground salience graph (FSG) to characterize the similarity of an image patch to the bag-of-words background models in the temporal domain and to neighboring image patches in the spatial domain. We incorporate this similarity information into a graph-cut energy minimization framework for foreground object segmentation. The background-foreground classification results at neighboring frames are fused together to construct a foreground probability map to update the graph weights.

## Demo

<iframe width="420" height="315" src="https://www.youtube.com/embed/FKXBs6Qdx2M" frameborder="0" allowfullscreen></iframe>



## Reference

Zhang, Zhi, Tony X. Han, and Zhihai He. "**Coupled ensemble graph cuts and object verification for animal segmentation from highly cluttered videos.**" Image Processing (ICIP), 2015 IEEE International Conference on. IEEE, 2015.

Ren, Xiaobo, Tony Han, and Zhihai He. "**Ensemble video object cut in highly dynamic scenes.**" Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. 2013.
