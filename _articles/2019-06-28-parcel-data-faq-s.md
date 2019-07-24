---
weight: 0
category: Getting Started
published: false
title: Parcel Data - FAQ's
---

## Frequently Asked Questions (FAQ) About Landgrid Parcel Data

**Where does your County data come from?**

We source our data directly from each County or whom they designate as the official source for their parcel data.

**A few Counties are missing from your data set but are labeled as “Available”, what does that mean?**

Available County data means that we have confirmed the data is available from the County, but for some reason we did not obtain the data. The main reason is usually cost from the County. Some Counties intentionally price their County data very high for various reasons. If you are interested in a missing County, any missing County, please let us know and we will update our research to confirm pricing (sometimes it goes down from our initial research findings) and work something out with you to obtain and standardize that data.

**Do you have X data for Y County?**

A current, detailed list of every County in the US and what data fields we have for each is always available at the following URL. This spreadsheet can be downloaded as a CSV for closer analysis:  [https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/](https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/)

**How do you standardize the data provided by the Counties?**

The main way we make county data much easier to work with is by standardizing the column names of the raw data provided by each county. We do not standardize the values in most columns, most we keep those exactly as provided by the county, but we do make sure that every county in our system is converted to a standard table schema, with consistent column names across the nationwide dataset. Please see “What is the Landgrid Standard Schema?” question below.

In addition, we do further standardize the parcel address fields using the USPS database of addresses in the US. That makes sure addresses are uniform and as correct as they can possible be. Because we require an address to match a known address in the USPS database before we further standardize it, not every address in a county is standardized. Typically 60% - 95% of the addresses in a county can be directly matched in the USPS system and therefore are fully standardized in our dataset.

**What is the Landgrid Standard Schema?**

We standardize column names for easy access across every county in our nationwide dataset. This is what we call the Landgrid Standard Schema.

Our initial Standard Schema, (v1 or 1.0), was 4 columns standardized: parcel geometry, parcel id, owner, situs address. Those 4 fields are standardized across 100% our nationwide dataset.

We are currently using version 3 (v3 or 3.0) of our Standard Schema and it standardizes the column names for 80 county provided data columns, and 20 Landgrid provided data columns. This schema is applied to approximately 60% of our dataset at this time (July 2019) and should be rolled out to rest of our dataset in the next 6 - 12 months. A data dictionary for both of these schemas is available: [https://docs.google.com/spreadsheets/d/14RcBKyiEGa7q-SR0rFnDHVcovb9uegPJ3sfb3WlNPc0/edit#gid=1010834424](https://docs.google.com/spreadsheets/d/14RcBKyiEGa7q-SR0rFnDHVcovb9uegPJ3sfb3WlNPc0/edit#gid=1010834424)

**When was your data last updated?**

Our initial nationwide dataset was collected in the 2015-2016 time frame and we still have some data from that time period, however, approximately 57% of our data has been refreshed in the last year (as of July 2019), and we expect to have the remainder updated in the next 12 months, with an increasing frequency of updates after that.

We make every effort to update our data at least yearly, with major metro areas being updated twice a year. Going forward, we will be increasing the frequency of data updates to better match the individual County update schedules.

All data is tracked with the date of “last refresh” from the County. 

A detailed listing of every County in the US and the date we last refreshed directly from the County is always available. This spreadsheet can be downloaded as a CSV for closer analysis: [https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/](https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/)

**What processes do you use to standardize and normalize your addresses?**

We primarily work with addresses provided directly from the County. The County address data is separated out, or combined, to populate the typical address fields in use, address line 1, address line 2, city, state, zip. Basic text cleaning is done at that same time to remove special or non-printing characters.

Where counties have not provided full addresses for parcels, we use US Census data to fill in missing zip codes and cities.

Parcel addresses are then passed through a USPS address verification system which further normalizes and standardizes the address to USPS guidelines where a match was made against the USPS database of addresses. Non matching address are left as they were sent by the County.

The original County provided raw address data is always retained unaltered and included on the parcel record.


## API Access

**What is an API and why might I use one?**

API stands for Application Programming Interface, and is for use by software developers to interact directly with our national dataset. They are usually used when someone wants to automate some process that interacts with our national parcel dataset. All APIs require programming work to make them useful in any particular use case scenario.

**What APIs does Landgrid make available?**

We provide two different APIs for working with our data. Please remember, all APIs are intended for use by software developers and are not for end users’ direct use. All APIs require programming work to make them useful in any particular use case scenario.

Tile Map Service (TMS) Layer - This is an interactive, visual rendering of our dataset, for use in web or desktop applications where using the parcels overlaid on other layers is useful. Landgrid’s TMS layer is in Mapbox Vector Tile (.mvt) format. [https://docs.mapbox.com/vector-tiles/reference/](https://docs.mapbox.com/vector-tiles/reference/)

RESTful API - This is a typical stateless, client/server based API that supports retrieving parcel shape and meta data using lat / lon coordinates, among other options. Please see [https://support.landgrid.com/articles/using-the-api/](https://support.landgrid.com/articles/using-the-api/) for a complete reference to the API.