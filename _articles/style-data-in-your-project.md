---
weight: 1
category: Managing Data
published: true
intro: Use Styles to color code parcels
title: Style Data in Your Project
---
_This feature is only available with a Landgrid Pro, Team, or Enterprise account. [Click here to upgrade your account](https://landgrid.com/plans)._

If you want to create a parcel map color coded based on data in your account (either survey data or imported data) you can do so by creating Styles rules. Styles rules will apply to your entire Project. You can change your Styles at any time.

Styles rules are matched to parcels sequentially based on the top to bottom order in your Project's Styles area. That means if you create a set of Styles rules that includes two color codes, both of which match parcels on your Project, the parcels will be highlighted ONLY by the color rule you defined first. Any parcel with imported data not covered by a Styles rule will show up in the "default" color, which you can also designate.

![Style_img.jpg]({{site.baseurl}}/img/Style_img.jpg)


For example:

Say you have a parcel with the address 555 Fake Street that has two data fields:

Condition: Good
Occupancy: Vacant

If you go to my Styles area and set Condition = Good to color parcels in Green, and then set another rule to color Occupancy = Vacant parcels in Red, then my 555 Fake Street parcel will ONLY color in Green -- it matches both rules, but the Condition rule is set first, so that's the color that will be applied.

A legend on the left hand sidebar (under "Overview") will explain your style rules, pulling information from your spreadsheet and the rules you set. If you plan to share your Project (See "Share Your Project"), you may want to check that your column headers and cell contents are easily comprehensible before importing the data.

If you want to search your data in a way that will show all properties that match BOTH Condition = Good AND Occupancy = Vacant, then skip to Query to learn about searching multiple criteria on landgrid.com.
