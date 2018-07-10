---
weight: 1
category: Adding Data
published: true
intro: How to add data to your map by importing a CSV
title: Add Data via CSV
---
With the Land Grid you can import data from CSVs and Excel spreadsheets to visualize, query, and work with the data in a parcel map setting.

**NOTE:** Currently, we require data sources to contain a column with Parcel IDs so we can match data to properties we have online. More data-matching methods will be coming online soon.
**NOTE** Uploading data works much better if source datasets contain a column with Parcel IDs so we can match precisely. It is possible to match with latitude/longitude or by address, but the margin of error is likely to be higher.

Below is a step-by-step guide to importing data from a CSV or Excel spreadsheet:

Click on the project you’d like to upload data to. From the left sidebar, click “Data” and then the “Import Data” button. 
Click “Select a File” and navigate to the desired dataset’s location. Click “Import”.
Once the data preview appears, select the column that contains the Parcel ID (we’ll try to guess, but make sure it’s correct) 
Based on the parcel IDs in your data, we’ll try to determine the city you’re importing data to – make sure this is correct and click the city that appears that matches the data you’re importing. Click “Finish”, and standby for importing to complete (progress bars on right side of screen will show status).

Below is an animation showing how to connect import a CSV of data:

![qp7IabrGKl.gif]({{site.baseurl}}/img/qp7IabrGKl.gif)


**NOTE:** Larger datasets can take a while to upload, and there is a max of 200,000 rows of data that you can add to a map. (if you are working on a specific project that requires a huge dataset, let someone from the Loveland team know and we may be able to help you).

Once you return to your map, an alert box in the top right of your screen will show progress as data is added to your map. When data importing is complete, you'll see the boundaries that contain imported data shade in a new color to denote that there is now data within that boundary.
