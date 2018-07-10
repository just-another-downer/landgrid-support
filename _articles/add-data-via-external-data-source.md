---
weight: 1
category: Adding Data
published: true
intro: How to connect an external data source to your map
title: Add Data via External Data Source
---
The Land Grid supports several open data sources and is working to support ever more. Here is a list of platforms you can currently connect to the Land Grid maps:

[ESRI Open Data Portals](http://opendata.arcgis.com/)  
[Socrata Open Data Portals](https://socrata.com/)   
[Enigma](http://enigma.io/)  

**NOTE:** Currently, we require data sources to contain a column with Parcel IDs so we can match data to properties we have online. More data-matching methods will be coming online soon.

Each data source has a slightly different process for connecting a dataset. You can see instructions for each by navigating to **Manage Map --> Import** and clicking on the data source you want to connect. Below is a generalized step-by-step guide to importing data:

  1. Click "Manage Map"
  2. Click "Import"
  3. Select the platform from which you'd like to import data.
  4. Follow instructions to collect the API, URL, GeoJSON or other link needed to c connect the dataset to Site Control.
  5. Paste link where text box says "Put the dataset link here!"
  6. Click "Connect"
  7. Once the data preview appears, select the column that contains the Parcel ID (we'll try to guess, but make sure it's correct)
  8. Based on the parcel IDs in your data, we'll try to determine the city you're importing data to -- make sure this is correct and click the city that appears that matches the data you're importing
  9. Click "Finish"
  10. Click "See Results on Your Map"
  11. Standby for importing to complete (alert box in upper right of screen will show progress)

Below is an animation showing how to connect a map to a dataset stored in an ESRI Open Data Portal. In this example, the Land Grid map called "Detroit Foreclosures" is connected to a dataset that was created by LOVELAND's local data partners, Data Driven Detroit, and hosted on their ESRI portal:

![pJQqbPxmub.gif]({{site.baseurl}}/img/pJQqbPxmub.gif)

**NOTE:** Once you connect a data source, the Land Grid will begin to import data when you click "See The Results on Your Map". Larger datasets will take a while, and there is a max of 200,000 rows of data that you can add to a map.

Once you return to your map, an alert box in the top right of your screen will show progress as data is added to your map. When data importing is complete, you'll see the boundaries that contain imported data shade in a new color to denote that there is now data within that boundary.
