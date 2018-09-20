# Chipy Mentorship Fall 2018: Blog 1

### Why am I here?
I love maps, but I don't get to work on geospatial problems professionally.

My geospatial skills are out of date.

I want to improve my Python skills.

## My Project

I would like to explore different modes of transportation in Chicago and the network they form. I am particularly interested in incorporating Divvy. Google Maps does not include Divvy as a transit option, so I want to see if I can incorporate bike share into the routing for all or part of a given trip. I also want to look at ridership data to identify popular routes. 

## Research Python Geospatial Packages

The world of geospatial analysis has changed _a lot_ since I studied it a decade ago! There is a whole world of open source geospatial tools in Python that I wanted to explore. In fact, there are far too many for me to get anything close to a comprehensive overview in the 3 month period of the mentorship. After a bit of research here are some of the tools I'll be using to complete my project:

**[GeoPandas](http://geopandas.org/)**: This package enables spatial operations with the GeoDataFrame structure, an extension of the Pandas DataFrame. I am already familiar with DataFrames, so being able to perform operations like intersect and spatial overlay with a similar structure is _awesome_.

**[OSMnx](https://github.com/gboeing/osmnx)**: Obtaining street network datasets used to be fairly difficult - a lot of it was proprietary - but [Open Street Map](https://www.openstreetmap.org) has really changed the landscape. OSMnx makes it _so simple_ to access topological data sourced from Open Street Map:

  ```python
  import osmnx as ox

  G = ox.graph_from_place('Chicago, Illinois, USA', network_type='drive')
  ```

**[contextily](https://github.com/darribas/contextily)**: Real talk, I've never been great at making pretty maps. I am always much more interested in the analysis than the visual appeal of the final product. Contextily allows me to use pre-existing map tiles as a background.

## Gather Data

I will be sourcing most of my datasets from Chicago's Open Data Portal. Here is what I have so far:
 - **CTA Rail**:
     - Stations (shapefile)
     - Lines (shapefile)
     - Daily ridership by station (CSV)
        - I'm not able to access this via API because the station IDs in the Station shapefile don't match what's available in the ridership API. Fun!
 - **CTA Bus**:
     - Stops (shapefile)
     - Routes (shapefile)
     - Daily ridership by route (API)
 - **Divvy**:
     - Dock locations (CSV for historical, API for real-time)
     - Historical rides (CSV)

As I mentioned above, I'll also be using network data from Open Street Map via OSMnx. I can change the  `network_type` parameter to get walking and biking networks well. 


## Explore GeoPandas

## What's Next?

I have a fair bit of data-janitoring and data collection still ahead. 
 - **Reconcile CTA Rail Ridership with CTA Station locations**
    Because these two datasets to not have a common key to identify stations, I will need to find an alternate way to join them. I attempted to use `station_name` but these are not consistent and are not unique to each station. For example, the Damen stop on the Blue Line is different from the Damen stop on the Red Line. 
 - **Approximate rail and bus travel times**
   The CTA has an API with real-time bus and train locations and arrival times. I can use this to gather data and approximate the travel time between each bus stop or train station. This API has a limit of 10,000 calls per day so I will not even come close to covering the entire system. I will need to choose a few routes and lines and gather data for a few hours and then extrapolate from there. This method isn't great for travel time accuracy, but this was the best option given the data available and limited time. 
   
 And once data collection is complete I'll start building my network. I'll be looking for intersections and distances between the different transit mode datasets - the beginnings of a network. 
