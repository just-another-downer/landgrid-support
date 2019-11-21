---
weight: 0
section: Parcel Data
category: Overview
published: true
title: Our schema & quality
---

We make county data easier to work with by standardizing the column names of the raw data provided by each county.

[You can browse the latest version of the Loveland standard schema online here.](https://docs.google.com/spreadsheets/d/14RcBKyiEGa7q-SR0rFnDHVcovb9uegPJ3sfb3WlNPc0/edit#gid=1010834424)

We do not standardize the values in most columns. Most we keep those exactly as provided by the county, but we do make sure that every county in our system is converted to a standard table schema, with consistent column names across the nationwide dataset.

Some counties come with columns that don't fit in our extensive standard schema but may be useful. We include these columns as-is in our exports. However, we do not have a data dictionary for these fields. We recommend only working with the standard schema columns unless you have a pressing need for these additional columns.

### Quality control

Data quality varies widely from county to county, and we take numerous automatic and manual steps to give you the cleanest data we can. At the same time, we work to preserve the core facts delivered by the county.

Our import systems automatically clean invalid values like bad dates, null values, and empty strings. We also validate and geometries across the entire dataset.

### Address standardiziation

We take extra steps to standardize and validate addresses. The County-provided parcel address data is transformed to populate the typical address fields. Basic text cleaning is done at that same time to remove special or non-printing characters.

Where counties have not provided full addresses for parcels, we use US Census data to fill in missing zip codes and cities.

Parcel addresses are then passed through a USPS address verification system which further normalizes and CASS-standardizes the address to USPS guidelines where a match was made against the USPS database of addresses. Non-matching address are left as they were sent by the County.

The original County provided raw address data is always retained unaltered and included on the parcel record.
