---
weight: 0
category: Getting Started
published: true
title: FAQ's - Parcel Data
---

## Frequently Asked Questions (FAQ) About Landgrid Parcel Data

**Where does your County data come from?**

We source our data directly from each County or whom they designate as the official source for their parcel data.

**Some Counties are missing from your data set but are labeled as “Available”, what does that mean?**

Available County data means that we have confirmed the data is available from the County, but for some reason we did not obtain the data. The usual reason is cost from the County, some Counties  price their parcel data very high. If you are interested in any missing County, please let us know and we will update our research to confirm costs or other changes and work something out with you to obtain and standardize that data.

**Do you have X data for Y County?**

A current, detailed list of every County in the US and what data fields we have for each is always available at the following URL. This spreadsheet can be downloaded as a CSV for closer analysis:  [https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/](https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/)

**How do you standardize County data generally?**

The main way we make county data much easier to work with is by standardizing the column names of the raw data provided by each county. We do not standardize the values in most columns, most we keep those exactly as provided by the county, but we do make sure that every county in our system is converted to a standard table schema, with consistent column names across the nationwide dataset. Please see “What is the Landgrid Standard Schema?” question below.

In addition, we further standardize the parcel address fields using the US Postal Service database of addresses. For details on address specific standardization please see the "How do you standardize and normalize addresses?" question below. 

**What is the Landgrid Standard Schema?**

We standardize column names for easy access across counties in our nationwide dataset in to our Standard Schema for tables.

Our initial Standard Schema, (v1 or 1.0), was 4 columns standardized: parcel geometry, parcel id, owner, situs address. Those 4 fields are standardized across 100% our nationwide dataset.

We are currently at version 3 (v3 or 3.0) of our Standard Schema and it standardizes the column names for 80 county provided data columns, and 20 Landgrid provided data columns. This schema is applied to approximately 60% of our dataset at this time (July 2019) and should be rolled out to rest of our dataset in the next 6 - 12 months. A data dictionary for both of these schemas is available: [https://docs.google.com/spreadsheets/d/14RcBKyiEGa7q-SR0rFnDHVcovb9uegPJ3sfb3WlNPc0/edit#gid=1010834424](https://docs.google.com/spreadsheets/d/14RcBKyiEGa7q-SR0rFnDHVcovb9uegPJ3sfb3WlNPc0/edit#gid=1010834424)

**When was your data last updated?**

Our initial nationwide dataset was collected in the 2015-2016 time frame and we still have some data from that time period. However, approximately 57% of our data has been refreshed in the last year (as of July 2019), and we expect to have the remainder updated in the next 12 months, with an increasing frequency of updates after that.

We make every effort to update our data at least yearly, with major metro areas being updated twice a year. Going forward, we will be increasing the frequency of data updates to better match the individual County update schedules.

All data is tracked with the date of “last refresh” from the County. 

A detailed listing of every County in the US and the date we last refreshed directly from the County is always available. This spreadsheet can be downloaded as a CSV for closer analysis: [https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/](https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/)

**How do you standardize and normalize addresses?**

The County provided parcel address data is transformed to populate the typical address fields in use, address line 1, address line 2, city, state, zip. Basic text cleaning is done at that same time to remove special or non-printing characters.

Where counties have not provided full addresses for parcels, we use US Census data to fill in missing zip codes and cities.

Parcel addresses are then passed through a USPS address verification system which further normalizes and standardizes the address to USPS guidelines where a match was made against the USPS database of addresses. Non matching address are left as they were sent by the County.

The original County provided raw address data is always retained unaltered and included on the parcel record.


## API Access

**What is an API and why might I use one?**

API stands for Application Programming Interface, and is for use by software developers to interact directly with our national dataset. They are usually used when someone wants to automate some process that interacts with our national parcel dataset. All APIs require programming work to make them useful for any specific application.

**What APIs does Landgrid make available?**

We provide two different APIs for working with our data. Please remember, all APIs are intended for use by software developers and are not for end users’ direct use.

Tile Map Service (TMS) Layer - This is an interactive, vecotr rendering of our dataset, for use in web or desktop applications where using the parcel shapes overlaid on other layers is useful. Landgrid’s TMS layer is in Mapbox Vector Tile (.mvt) format. [https://docs.mapbox.com/vector-tiles/reference/](https://docs.mapbox.com/vector-tiles/reference/)

RESTful API - This is a typical stateless, client/server based API that supports retrieving parcel shape and meta data using lat / lon coordinates, among other options. Please see [https://support.landgrid.com/articles/using-the-api/](https://support.landgrid.com/articles/using-the-api/) for a complete reference to the API.