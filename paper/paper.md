---
title: 'Nodule Analysis: A Fiji plugin for nodule data collection'

tags:
  - Java
  - ImageJ
  - FIJI
  - biology
  
authors:
  - name: Brandin Farris
    orcid: 0009-0002-2462-6094
    equal-contrib: true
    affiliation: "1, 2" # (Multiple affiliations must be quoted)
  - name: Bala Krishnamoorthy
    orcid: 0000-0002-2727-6547
    equal-contrib: false # (This is how you can denote equal contributions between multiple authors)
    affiliation: "1"
    
affiliations:
  - index: 1
    name: Oregon State University
  - index: 2
    name: Washington State University
    
date: 21 February 2026

bibliography: paper.bib
---

# Summary

When performing analysis on images of the root systems of hundreds of plants, it is useful to have a high throughput method for gathering directly observed and inferred data from the roots.
Fiji is a java based software extending ImageJ2 for performing analysis on biological images [@fiji1].
Nodule Analysis is a set of two Fiji (ImageJ2) plugins (Nodule Segmentation and Nodule Distances) that provides a method for computing the counts, areas, and pair-wise distances along the root system of all of the nodules on an image of a root system using various data gathering methods. 
The plugin utilizes part of Weka's FIJI plugin, particularly their unsupervised color clustering method to segment the nodules and the root system separately[@Weka]. 


# Statement of need

Nodule Segmentation integrates with ImageJ2, and is designed to segment, categorize, and count nodules on images of plants with attached nodules under fluorescent lighting. Nodule Distances takes the output from Nodule Segmentation and computs pair-wise distances between nodules along the root system. These plugins were designed to provide a UI-based approach for converting 2d images into data amenable to analysis. 
There are other software that provide similar functionality such as [@RootPainter] and [SNAP], but they do not provide a UI to manually correct mistakes, and both use Machine learning which requires training a model on a given data set. We wanted to provide the community an unsupervised method for data processing for data sets that were too small to train on or to avoid the manual labor of training a model.
Additionally, to the best of our knowledge, there is currently no plugin that takes images of plants and computes the distances between marked objects on the plant along the plant's branches.


# State of the Field

ImageJ2 is an open-source, java based program for image analysis of biological images. Nodule Segmentation is an ImageJ2 plugin designed using the ImageJ API so as to integrate with the rest of the eco-system for biology-based imaging. 

There are currently no unsupervised methods that automates the collection of nodule counts, sizes, and distances between nodules along the root system.
Root Painter is a program that utilizes deep learning to perform segmentation of a variety of biological images [@RootPainter].
Root Painter has been shown to count nodules effectively, with relatively small error ($R^1 = 0.69$), but it does not provide a way to improve the segmentation, and does not compute their area. Additionally, it utilizes machine learning to improve the output of the data.

Nodule Segmentation was built rather than contributing to an existing project for several reasons. an unsupervised method for segmentation with some automated post-processing methods to improve the segmentation provides the community with an option that does not require training. Additionally, we wanted to designa a method that computes the area as opposed to just the counts. Furthermore, the user is granted an opportunity to make changes to the output of the data before the plugin saves the results, resulting in an entire pipeline to convert images into analysis-ready data without requiring the user to write code or train a model. 


# Software Design

When designing Nodule Segmentation, we wanted a system that was user friendly and accessible to people without knowledge in programming. For that reason we created a pipeline that takes user input and does the entire analysis, occasionally asking the user for additional input as needed. The philosophy was to design the plugin to do one thing well as opposed to taking a generally module approach. We did however allow users to create their own unsupervised segmentation file to allow for the segmentation of nodule images that used different imaging techniques. This allows datasets with different design setups to utilize the plugins. The Nodule Distances plugin was designed for the purpose of computing pair-wise distance calculations along the root system, and has a class for computing statistics using those distances. This class was designed to easily allow others to contribute further statistical calculations either inside or outside of the plugin itself. 

# Research Impact Statement

The Nodule Segmentation plugin was used by Niall Miller in his PhD thesis. The Nodule Distances plugin was used on the same data set and is being analyzed by Brianna Banting, with a paper in progress. Both of these projects originated from the Stephanie Porter Lab at Washington State University.


# AI Usage Disclosure

AI was used in the creation of this code. AI was used to reference documentation, assist in writing parts of the code, and in adding descriptive comments/documentation. AI was never asked to make entire methods, and any code that was copy-pasted was read thoroughly and tested to ensure quality. To ensure correctness of code, AI was only asked to do small tasks at a time, such that any code was easily verifiable. AI was not used in the writing of this paper, but was used in the creation of the bibliography. All bib entries were verified.

# Acknowledgments

This project was funded by the Porter Lab from Washington State University and 
the development was aided by Niall Miller and Brianna Banting. 

# References