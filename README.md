# Chipy Mentorship Fall 2018: Blog 1

## My Project

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
     - Daily ridersip by station (CSV)
        - I'm not able to access this via API because the station IDs in the Station shapefile don't match what's available in the ridership API. Fun!
 - **CTA Bus**:
     - Stops (shapefile)
     - Routes (shapefile)
     - Daily ridersip by route (API)
 - **Divvy**:
     - Dock locations (CSV for historical, API for real-time)
     - Historical rides (CSV)
As I mentioned above, I'll also be using network data from Open Street Map via OSMnx. I can change the  `network_type` parameter to get walking and biking networks well. 


## Explore GeoPandas

## What's Next?



## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/lauralevy/chipymentorship/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/lauralevy/chipymentorship/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
