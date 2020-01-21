---
weight: 0
category: Getting Started
published: true
title: FAQs - Parcel Data
---

## Frequently Asked Questions (FAQ) About Landgrid Parcel Data

**Where does your County data come from?**

We source our data directly from each County or whom they designate as the official source for their parcel data.

**Some Counties are missing from your data set but are labeled as “Available”, what does that mean?**

Available County data means that we have confirmed the data is available from the County, but for some reason we did not obtain the data. The usual reason is cost from the County, some Counties  price their parcel data very high. If you are interested in any missing County, please let us know and we will update our research to confirm costs or other changes and work something out with you to obtain and standardize that data.

**Do you have "this" attribute for "this" County?**

A current, detailed list of every County in the US and what data fields we have for each is always available at the following URL. This spreadsheet can be downloaded as a CSV for closer analysis:  [https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/](https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/)

**How do you standardize County data generally?**

The main way we make county data much easier to work with is by standardizing the column names of the raw data provided by each county. We do not standardize the values in most columns, most we keep those exactly as provided by the county, but we do make sure that every county in our system is converted to a standard table schema, with consistent column names across the nationwide dataset. Please see “What is the Landgrid Standard Schema?” question below.

In addition, we further standardize the parcel address fields using the US Postal Service database of addresses. For details on address specific standardization please see the "How do you standardize and normalize addresses?" question below. 

**What is the Landgrid Standard Schema?**

We standardize column names for easy access across counties in our nationwide dataset in to our Standard Schema for tables.

We are currently at version 5 of our Standard Schema and it standardizes the column names for approximately 80 county provided data columns, and 25 Landgrid provided data columns. This schema is applied to 100% of our dataset. A data dictionary is available: [https://docs.google.com/spreadsheets/d/14RcBKyiEGa7q-SR0rFnDHVcovb9uegPJ3sfb3WlNPc0/edit#gid=1010834424](https://docs.google.com/spreadsheets/d/14RcBKyiEGa7q-SR0rFnDHVcovb9uegPJ3sfb3WlNPc0/edit#gid=1010834424)

**When was your data last updated?**

Approximately 82% of our data has been refreshed in the last year (as of January 15, 2020), and we are working to have the remainder updated as soon as possible, with an increasing frequency of updates after that.

We make every effort to update our data at least yearly, with major metro areas being updated twice a year. Going forward, we will be increasing the frequency of data updates to better match the individual County update schedules.

All data is tracked with the date of “last refresh” from the County. 

A detailed listing of every County in the US and the date we last refreshed directly from the County is always available. This spreadsheet can be downloaded as a CSV for closer analysis: [https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/](https://docs.google.com/spreadsheets/d/1q0PZB72nO8935EMGmsh3864VjEAMUE-pdHcPkoAiS5c/)

**How do you provide data updates?**

All bulk data is provided via SFTP as zip files of each county in the format of your choice (GeoPKG, CSV, GeoJSON, etc), using a pull model. We organize things on a county by county basis using the county's FIPS code (`geoid` in our standard schema columns). We add or refresh 20-300 counties every month with data from the county source.

Each month we replace the existing county zip file in a client's download directory with the refreshed county files.

We send out an email each month listing the counties that were refreshed, as well as an updated listing of all the counties and their `last_refresh` date, which is the last date we updated the data directly from the source.

We also provide a CSV file of our VERSE table that lists the `last_refresh` date for each county.

On each parcel we provide a `'ll_uuid` number that permanently and uniquely identifies each parcel across data refreshes and updates. The `ll_uuid` can be used to match any locally stored parcels with updated parcels in the county file.

We also make improvements to the data that does not come directly from the county, like standardizing addresses, cleaning out non-standard characters, adding additional data attributes, etc. We generally re-export our full dataset quarterly to reflect those changes. Improvements we make to data does NOT affect the `last_refresh` of a county, that is always the date we last pulled data directly from the source. Notices of full dataset exports are also included in the monthly email update sent to all clients.


**How do you standardize and normalize addresses?**

The County provided parcel address data is transformed to populate the typical address fields in use, address line 1, address line 2, city, state, zip. Basic text cleaning is done at that same time to remove special or non-printing characters.

Where counties have not provided full addresses for parcels, we use US Census data to fill in missing zip codes and cities.

Parcel addresses are then passed through a USPS address verification system which further normalizes and standardizes the address to USPS guidelines where a match was made against the USPS database of addresses. Non matching address are left as they were sent by the County.

The original County provided raw address data is always retained unaltered and included on the parcel record.

## Buildings and area calculations

**How do you determine the Loveland Building Count value (`ll_bldg_count`)?**

We work with [Gateway Spatial](https://gatewayspatial.com/sample-page/), a data firm that collects and curates building footprint data sets directly from counties in the US. They provide one of the most comprehensive, authoritative building footprint nationwide layers available. 

We then process that footprint data set with our parcel shapes data set to determine how many buildings are on the parcel.

Combining two large data sets, each of which is a combination of a few thousand smaller data sets, to derive a value is always a challenge and we do our best to be as accurate as possible, but some things to keep in mind when working with the building count data:
1. Each county determines what buildings to track in their GIS system. These are considered by the county to be the significant structures on the parcel. Some counties will include every structure regardless of size, some will only track houses and garages for example.
1. Much like county parcel data, counties refresh footprint data on their own individual schedules, and less frequently than parcel data in our experience. We do not yet have a way to track the 'last_refresh' date of the building footprint data by county.

**How do you calculate the parcel acres, parcel square feet, and building square feet (`ll_gisacre`, `ll_gissqft`, `ll_bldg_footprint_sqft`)?**

We projected each parcel and building footprint into its UTM Zone SRS, calculated the area in meters and converted that to acres and sqft. This should provide a relatively uniform and consistent value across the US.

## Loading bulk data

**How do you load all of these files into a database?**
We generally work in a GNU/Linux environment using the command line. Our internal workflow makes use of the OSGeo Foundation libraries and tools including GDAL/OGR and PostGIS for PostgreSQL. The OSGeo project also provides an MS Windows 10 installer for using the tools on a Windows machine named OSGeo4Win.

The `ogr2ogr` command line tool is the best way to import data into a PostgreSQL/PostGIS or MS SQL Server database.

Below is a typical command line to cycle through a set of GeoDB files and append them to a table in PostgreSQL:
~~~~
for gdb in /path_to_files/*.gdb ; 
do echo "$gdb" ; 
  ogr2ogr -f "PostgreSQL" PG:"dbname=dbname" $gdb -progress --config PG_USE_COPY YES -nln public_schema.target_table_name -append ; 
done
~~~~

Using ogr2ogr to load parcel data into a MS SQL Server works the same way. Parcel data should use the `geometry` data type in MS SQL Server. A good example of how to do that is [this blog post by Alastair Aitchison](https://alastaira.wordpress.com/ogr2ogr-patterns-for-sql-server/). They also cover installing the OSGeo4Win environment. 

The main item of the command line options are the database connection options. You will have to make sure the user name and password are available and that the client can actually connect to the database and has all the needed permissions. For PostgreSQL on GNU/Linux, there are standard PG_* environmental variables and the .pgpass file for storing credentials that will work with the ogr2ogr commands so they do not have to be included in the command line.


## API Access

**What is an API and why might I use one?**

API stands for Application Programming Interface, and is for use by software developers to interact directly with our national dataset. They are usually used when someone wants to automate some process that interacts with our national parcel dataset. All APIs require programming work to make them useful for any specific application.

**What APIs does Landgrid make available?**

We provide two different APIs for working with our data. Please remember, all APIs are intended for use by software developers and are not for end users’ direct use.

Tile Map Service (TMS) Layer - This is an interactive, vecotr rendering of our dataset, for use in web or desktop applications where using the parcel shapes overlaid on other layers is useful. Landgrid’s TMS layer is in Mapbox Vector Tile (.mvt) format. [https://docs.mapbox.com/vector-tiles/reference/](https://docs.mapbox.com/vector-tiles/reference/)

RESTful API - This is a typical stateless, client/server based API that supports retrieving parcel shape and meta data using lat / lon coordinates, among other options. Please see [https://support.landgrid.com/articles/using-the-api/](https://support.landgrid.com/articles/using-the-api/) for a complete reference to the API.
