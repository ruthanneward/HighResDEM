# Creating a high-resolution DEM from LiDAR data
## Author: Ruthanne Ward
## Organization: Cooperative Institute for Great Lakes Research 
## Date: August 2, 2024

### This repository explains how to create a high-resolution digital elevation model (DEM) from start to finish using your own data. This repository is a product of the NOAA Cooperative Institute of Great Lakes Research 2024 Summer Fellows Program.

**Downloading Data**

The best place to download high-quality LiDAR data is from the NOAA Digital Coast Data Access Viewer (https://coast.noaa.gov/dataviewer/#/). After navigating to this website: 
  1. Navigate to your area of interest and select the data you want to download.
  2. Once you have your data in your cart, select the preffered settings. Make sure to change "horizontal units" and "vertical units" to meters. Change "Output Product" to Points and "Output Format" to Points-LAZ. Select "Ground" in the "Data Classes" dropdown menu. Keep everything else the same unless you have a good reason to change it. Your final settings menu should look like this:
   ![image](https://github.com/user-attachments/assets/0cb7c437-9a80-4a52-81b9-096a25c33d96)

  3. Download this data. If you have a large area of interest you might need to repeat this process multiple times as there is a limit on how much data you can download at once. You will get an email that confirms your request and a second email once that request is completed. This can take a long time, sometimes over an hour. Sit tight, your data is on its way!

**Setting up a Conda Environment** 

You can set up the conda environment for this project two ways:
  1. Use the HighResDEM_env.yml file in this repo to set up your conda environment.
  2. Manually install the following packages:
       - numpy
       - rasterio
       - matplotlib
       - laspy[laszip]
    
**Creating the DEM from LiDAR**

  1. Unzip the .LAZ files. You can batch convert .LAZ files to .LAS files using https://github.com/LummiGIS/LAS_tools/blob/main/LAZ_to_LAS.py. If you are using bathymetric data as well as topographic data you can use the script I have included in this repo: LAZ_to_LAS_bathymetry.ipynb
  2. Convert the .LAS files into .tif files. You can do this using https://github.com/LummiGIS/Batch_LAS_to_Raster/blob/main/batch_las_to_raster.py. I run this script in my ArcGIS Pro Python Window. You can also install arcpy. I find it easier to run it directly in the ArcGIS Python Window.

**Correcting Bad Bathymetry Data** 

LiDAR data for bodies of water is not always the most accurate. If you intend to include bodies of water in your study area, this section is for you. If having accurate data for water bodies is not important to your project, feel free to skip to the next section. To replace the bathymetric LiDAR with higher accurate, lower resolution data: 
  1. Find bathymetry data for your area of interest. I used https://www.ncei.noaa.gov/products/great-lakes-bathymetry becuase my study area included the great lakes. NOAA has other great datasets for coastal bathymetry which can be found at this link https://www.ncei.noaa.gov/maps/bathymetry/.
  2. If you are just filling holes in your data skip this step. If you want to remove LiDAR bathymetry data before replacing it with other data you need to erase the water values from your DEM. I did this using the Erase and Extract by Mask tools in ArcPro. You can do this however you see fit.
  3. Next you are going to want to downscale the resolution of your new data to fit your DEM dervived from LiDAR and replace the novalue pixels with that new data. You can do that using the script I included in this repo: Overlay_DEMs.ipynb

**Visualizing your DEM** 
  1. You can visualize your DEM using the script I included in this repo: data_visualizing.ipynb
 
