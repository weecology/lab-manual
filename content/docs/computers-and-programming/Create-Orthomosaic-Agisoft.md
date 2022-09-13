# Orthomosiac Guide

Written by Ben Weinstein, September 13, 2022

The goal of this wiki is to document the steps to create a Orthomosaic from a set of UAV raw images. 
This relates to the everglades project with both Inspire Quadcopter and Wingtra Drones, but can serve as a general guide for the steps to create a georeferenced image.

# Agisoft
This tutorial uses Agisoft Metashape Pro. Future work needs to determine whether the standard version will suffice. 
We are following the manual here: https://www.agisoft.com/pdf/metashape-pro_1_7_en.pdf
This tutorial is quick and dirty in the sense that we are choosing low quality outputs to speed up the workflow.

## Load Images
Raw images look like:
<img width="1702" alt="Screen Shot 2022-09-13 at 11 19 35 AM" src="https://user-images.githubusercontent.com/1208492/189980044-8d168d05-5207-4880-9c4c-0773f91b6d70.png">

Workflow -> Add Folder
<img width="1630" alt="Screen Shot 2022-09-13 at 11 21 12 AM" src="https://user-images.githubusercontent.com/1208492/189980448-df8fabaa-e583-4b49-ac24-aa560fb6c8a8.png">

## Align Photos

Align photos places the images from a single physical camera into a common reference system. It creates a sparse point cloud of overlap to generally tell where the images are in space.

<img width="1765" alt="Screen Shot 2022-09-13 at 11 27 44 AM" src="https://user-images.githubusercontent.com/1208492/189981585-9d22162a-3090-46f6-8312-1aa294a1d4cc.png">

To view the coordinate system and alignment, view the 'reference' tab in the bottom left.
<img width="1486" alt="Screen Shot 2022-09-13 at 11 29 45 AM" src="https://user-images.githubusercontent.com/1208492/189982143-23d88091-a64b-4eed-a4df-1cd94040a3f9.png">

### Set Coordinate Reference System

We are confident that the Inspire knows its geospatial accuracy to about 10m, and the pitch degree to about 1m. 
<img width="1476" alt="Screen Shot 2022-09-13 at 11 38 42 AM" src="https://user-images.githubusercontent.com/1208492/189983775-5c3d4efa-d6a2-4c92-b3fc-4492810a44f7.png">

## Set Marker Points
If we don't have ground control points we can skip this step.

## Build Dense Cloud

Workflow -> Build Dense Cloud

The dense point cloud is required to build an elevation model to convert the 2D images into a 3d surface. 

## Build Digital Elevation Model

The elevation model projects the images into 3D space and is saved as a seperate .tif file.

Workflow -> Build DEM

## Build Orthomosaic

Use the digital elevation model and the dense point cloud to create a single stitched model of the entire colony.

<img width="1651" alt="image" src="https://user-images.githubusercontent.com/1208492/189990313-2fd7e259-e314-46b6-b811-e14a8e7795b2.png">

