# Data formats
```{post} 2021-07-19
:author: Adam R. Jensen
:tags: pvlib, solar, open science, gsoc
```

Two of the most important considerations is what kind of data you want to include and who (what) should be able to read the files. At this day and age it is a requirement that the file is easily parsed by software, though often it is nice to also be human-readable

Well what does it mean to be human-readable?

Aka. a file that you can open in a simple text editor and get a rough idea about the data it contains.


## File formats


### CSV

Do not do split data across multiple lines!!

Where should we keep the metadata? In the header, in the footer, in both?

Can be opened with Excel, quickly investigated and plotted by all!

CSV files typically have the extension .csv, though .txt or .dat may also used.

### JSON
A widely used fileformat, supposed to be 'human-readable'.

### NetCDF
A self-describing data format. The new kid on the block. The format that sounds ideal, but that few people know how to open.

I'm wondering if we have ourselves a chicken and the egg situation here - the dataformat is not widespread because few knows how to use it, and few knows how to use it because is isn't widespread.

NetCDF has become standard for xxx. It excells at geospatioal data, e.g., solar radiation for for a country at a given grid resolution. With more than a few grid points, this would become difficult to navigate in Excell or a csv file.

## Meatadata
First of all what metadata would we like to have?

Latitude and longitude should follow ISO 19115!

Timezone of the data.

## Timestamps
Generally we deal with time-series data, which means that each measurement is associated with a specific measurement time. This time can be either local time (with or without daylight savings) or UTC, which is generally prefered.

When thing that has been an issue is how to denote midnight. The standard convention is to label it 00:00, thoguth some formats, e.g. the University of Oregon SRML, denote it as 24:00. The latter convention makes it difficult to programmatically parse the data files, and requires effort in translating it to the former.


## Other considerations

### Platform agnogstic
Files should not be proprietary (such as MATLAB's file format .mat) and not only usable for specific libraries (such as the Pickle format for use with Pandas).

The files can be great to store temporary data or exchange data within a program, but they are not suitable for wider data distrubtion to the public.

