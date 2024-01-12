# Potential Natural & Actual Current Vegetation of Tenerife
_Practical, 22 January 2024 with [james.millington@kcl.ac.uk](mailto:james.millington@kcl.ac.uk)_

## 0. Introduction

While in Tenerife we visited multiple locations to see how vegetation varied across the island, considering the physical and human drivers of what influences both the potential natural vegetation (PNV) but also the actual current vegetation (ACV) on the island. In this practical we will use Google Earth Engine (GEE) and QGIS to create an initial simple map of PNV and ACV. As well as showing you how to use these tools to produce a professional map based on secondary data and your observations in the field, the practical will also help you to think about how to improve the simple map for your report (should you chose the Vegetation Coursework 2 Question – see the fieldtrip handbook).

By the end of this practical you should have:

1. Produced a simple PNV map of Tenerife using GEE;
2. Imported the simple PNV map into QGIS and created a shapefile to overlay the location of ACV;
3. Created a QGIS 'Layout' from the combination of 1 & 2 to produce a professional map that might be included in your report;
4. Understood and experimented how you could improve the initial outputs from 1 & 2 to produce an improved map for your report.

These objectives are laid out in the next four sections of this document, along with accompanying videos??. You should aim to finish sections 1-3 in the timetabled practical, to produce a map that looks something like Figure 1. You should then pursue improvements in the map (section 4) in any remaining time or after the practical while working on your report.

## 1. Creating a simple PNV map with GEE

In Term 1 you should have created a Google Earth Engine account that you then used with Emma Tebbs in the practical with her in Week 2 (see the KEATS message [here](https://keats.kcl.ac.uk/mod/forum/discuss.php?d=610870) if you did not do that – it can take several days for your account to be activated so if you do not already have an account you may have to work with a friend for the GEE parts of this practical). This practical builds on some of the things you did with Emma previously, so you may want to review the instructions for that practical quickly before starting here. For example, see the section _What is Google Earth Engine (GEE)?_ to remind yourself of the GEE basics.

  1.1 **Open Google Earth Engine** by visiting [https://code.earthengine.google.com/](https://code.earthengine.google.com/) and logging in with your account.

```javascript
//Centre the map on the coordinates of Tenerife, with a zoom of 10
var lon = -16.6192096994827;
var lat = 28.24084164623232;
var zoom = 10;
Map.setCenter(lon, lat, zoom)

//Get administrative area polygon for Tenerife and display
//Date described here: https://developers.google.com/earth-engine/datasets/catalog/USDOS_LSIB_2017
var dataset = ee.FeatureCollection('USDOS/LSIB/2017');              //create a dataset from the cloud data
var tenerifeBBox = ee.Geometry.Rectangle([-17, 27.9, -16, 28.6]);   //define a bounding box around Tenerife
var filtered = dataset.filterBounds(tenerifeBBox);                  //from the dataset select only data within the bounding box
var poly = filtered.geometry().coordinates().get(8);                //select only Tenerife's polygon (it's the 8th in the dataset) 
var tenerife = ee.Geometry.Polygon(poly);                           //create a polygon GEE recognises from the Tenerife polygon 
Map.addLayer(tenerife, {color: 'green',}, 'Tenerife')               //add the GEE polygon to the map
```

## 2. Import PNV map and create ACV shapefile in QGIS

## 3. Create a QGIS Layout for a professional map

## 4. Improve PNV and ACV maps
