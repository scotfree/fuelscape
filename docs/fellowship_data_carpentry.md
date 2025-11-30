class: center, middle, theme-dark
# Empower Yourself With Data!

* Reading & Writing used to be a Profession. So did Data Science.
* Data and Data Tools publicly available in astounding ways.
* Scientists, policymakers, and citizens now use many of the same tools.
 
      
  Scot Kennedy
      
  gateless@gmail.com
  
---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png)    
# Overview of Session

* Interesting and Open Data
* Useful and Open Tools
* Opening PandorAI's Box (sorry)
* Open Horizon
  
---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
# Interesting and Open Data

Not a comprehensive list but some places to get started and a glimpse at the depth and breadth of modern Open Data.

* Types and Formats
* Maps
* Climate and Environmental Datasets
* Cloud Data


---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
# Types and Formats
  * tab data and spreadsheets
  * geospatial data: vectors and rasters
    * try to get GeoJSON (vector) and GeoTIFF (raster) when you can
  * other
   
---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
# environmental and societal
  * https://data.humdata.org
  * https://jeiloh.github.io/esip_dlc_trusted_data/
  * Public, open-access data from NASA, NOAA, Copernicus, USGS, and many others.
  * [NASA](data.nasa.gov) hosts an incredible variety of climate-relevant datasets.
   
---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
# Maps and Geospatial Data 

* [Overture]()
  * Open Street Map
    * [Simple Maps](https://www.openstreetmap.org/search?query=rare+earth+mine&zoom=9&minlon=-117.60864257812501&minlat=34.30260622622907&maxlon=-113.40362548828126&maxlat=36.41686211530033#map=17/35.503225/-115.511230)
  * ([Turbi and Overpass](https://overpass-turbo.eu)
    * [OpenTopography](https://portal.opentopography.org/datasets) for landform and elevation data.

---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
#  huge and technical data in the cloud
* [AWS Open Data](https://registry.opendata.aws)
* Planet Labs for non-profits
* [NOAA](https://www.noaa.gov/information-technology/open-data-dissemination) uses cloud platforms


---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png)    
# Useful and Open Tools

* Free Athena Overture access in AWS/S3
* Notebooks
  * Jupyter Notebooks and Google Colab let anyone write and run code in a browser.
  * The notebook model lets you work from examples not write code. 
* DuckDB
* geojson.io and felt.com
  * export data from OSM or USGS 
* Don't forget Google Spreadsheets & friends - Earth/Maps, etc
  * ex: spreadsheet linked to map
* Put some data in AWS S3 and be amazed! There's an analysis ecosystem already pointed at it!
  * example: [Overture](https://docs.overturemaps.org/getting-data/) 
---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png)    
# Opening PandorAI's box
* Not talking about: specific ML & ANNs, AI for creative work
  * Try to make tools not answers
    * AI to make tools not analyze data - less waste and hallucination
* Have it Ask You Questions      
* Cautionary Tale: Board Game Rules
* Use AI to get you over the "energy barrier" for trying new things, not to do the work

---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
# Open Horizons and Examples

* A vector data example: 
  * San Francisco Bay Area cares about Tsunamis!
  * Get somve vectordata [here](https://maps.conservation.ca.gov/cgs/informationwarehouse/ts_evacuation/)
  * and look at it with [geojson.io](geojson.io)
 
* A raster data example:
  * Global "risk" [data](https://data.humdata.org/dataset/econai-conflict-forecast)
  * [Notebook](https://internal.fireatlas.org:8888/notebooks/fellowship_demo.ipynb) with some basic Geospatial tools in place
  * Try adding another [data set](https://data.humdata.org/dataset/global-wfp-food-prices/resource/d62af4be-cff6-437b-89a3-67f8fa4c53bf)

* Do some visualization
  * simple data here
  * empty notebook
  * use AI to build your visualization!
      
* Do some simple model building
  * similar 

Just wander:

* https://developers.google.com/earth-engine/datasets/catalog

Play:
* https://notebooks.gishub.org (start with "blog")
* https://felt.com
* https://www.epa.gov/enviroatlas/enviroatlas-dynamic-data-matrix
* https://colab.research.google.com/github/neuromatch/climate-course-content/blob/main/tutorials/W1D3_RemoteSensing/student/W1D3_Tutorial4.ipynb
      
