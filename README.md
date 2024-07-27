# Creating a high-resolution DEM from LiDAR data
## Author: Ruthanne Ward
## Organization: Cooperative Institute for Great Lakes Research 
## Date: August 8, 2024

### This repository explains how to create a high-resolution digital elevation model (DEM) from start to finish using your own data. This repository is a produce of the NOAA Cooperative Institute of Great Lakes Research 2024 Summer Fellows Program.

**Downloading Data**

The best place to download high-quality LiDAR data is from the NOAA Digital Coast Data Access Viewer (https://coast.noaa.gov/dataviewer/#/). After navigating to this website: 
  1. Navigate to your area of interest and select the data you want to download.
  2. Once you have your data in your cart, select the preffered settings. Make sure to change "horizontal units" and "vertical units" to meters. Change "Output Product" to Points and "Output Format" to Points-LAZ. Select "Ground" in the "Data Classes" dropdown menu. Keep everything else the same unless you have a good reason to change it. Your final settings menu should look like this:
   ![image](https://github.com/user-attachments/assets/0cb7c437-9a80-4a52-81b9-096a25c33d96)

  3. Download this data. If you have a large area of interest you might need to repeat this process multiple times as there is a limit on how much data you can download at once. You will get an email that confirms your request and a second email once that request is completed. This can take a long time, sometimes over an hour. Sit tight, your data is on its way!

**Setting up a Conda Environment** 

You can set up the conda environment for this project two ways:
  1. Use the environment.yml file in this repo to set up your conda environment.
  2. Manuall install the following packages:
         -

**Creating the DEM from LiDAR**

1. Unzip the .LAZ files. You can batch convert .LAZ files to .LAS files using https://github.com/LummiGIS/LAS_tools/blob/main/LAZ_to_LAS.py 
2. Convert the .LAS files into .tif files. You can do this using https://github.com/LummiGIS/Batch_LAS_to_Raster/blob/main/batch_las_to_raster.py. I run this script in my ArcGIS Pro Window. You can also install arcpy. I find it easier to run it directly in the ArcGIS Python Window.

**Correcting Bad Bathymetry Data** 

1. 
 
