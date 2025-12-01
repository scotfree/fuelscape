class: top-bottom-slide
background-image: url(vis_globalvapor.jpg) 
# Empower Yourself With Data!

* Reading & Writing used to be a Profession. So did Data Science.
* Data and Data Tools publicly available in astounding ways.
* Scientists, policymakers, and citizens now use many of the same tools.
 
      
  Scot Kennedy
      
  gateless@gmail.com
  
---
class: top-bottom-slide
background-image: url(vis_radar.png)    
# Overview of Session

See something cool, learn how much is available and open, share a tip.

* Interesting and Open Data; there is so much access to data.
* Useful and Open Tools: open source tools are now the best tools.
* Opening PandorAI's Box: using AI well is not trivial.
* Open Horizon: examples and exercises.
  
---
class: top-bottom-slide
background-image: url(vis_bubbles.png) 
# Interesting and Open Data

Not an exhaustive catalog but some places to get started and a glimpse at the depth and breadth of modern Open Data.

* Types and Formats
* Maps
* Climate and Environmental Datasets
* Cloud Data


---
class: top-bottom-slide
background-image: url(vis_weathermap.gif) 
# Types and Formats
  * tabular data and spreadsheets
    * CSV is universal and easy - it's just commas (or tabs, or whatever)
    * loads directly into spreadsheets and many other tools
    * just (big) text files, explore in your text editor!
  * geospatial data: vectors and rasters
    * rasters are continuous (like air pressure) and vectors are concrete shape and position (eye of storm, path of road)
    * try to get GeoJSON (vector) and GeoTIFF (raster) when you can
    * You can't hide from the Earth's curvature. Figure out your projection ("CRS")
  * other
    * ZIP and TGZ are just archives, easy to unzip 
    * JSON and YAML are wonderful and common, almost as easy to work with as CSV
   
---
class: top-bottom-slide
background-image: url(vis_sankey.png) 
# environmental and societal
  * https://data.humdata.org
  * https://jeiloh.github.io/esip_dlc_trusted_data/
  * [NASA](data.nasa.gov) hosts an incredible variety of climate-relevant datasets.
   
---
class: top-bottom-slide
background-image: url(vis_states.png) 
# Maps and Geospatial Data 
* [Overture]()
  * Open Street Map
    * [Simple Maps](https://www.openstreetmap.org/search?query=rare+earth+mine&zoom=9&minlon=-117.60864257812501&minlat=34.30260622622907&maxlon=-113.40362548828126&maxlat=36.41686211530033#map=17/35.503225/-115.511230)
  * ([Turbi and Overpass](https://overpass-turbo.eu)
    * [OpenTopography](https://portal.opentopography.org/datasets) for landform and elevation data.

---
class: top-bottom-slide
background-image: url(vis_streamgraph.png) 
#  huge and technical data in the cloud
* [AWS Open Data](https://registry.opendata.aws)
* Planet Labs for non-profits
* [NOAA](https://www.noaa.gov/information-technology/open-data-dissemination) uses cloud platforms
* [Kaggle](https://www.kaggle.com/datasets?fileType=csv) has a lot of random interesting datasets

---
class: top-bottom-slide
background-image: url(vis_vectorfield.png)    
# Useful and Open Tools
* Free Athena Overture access in AWS/S3
* Notebooks Are An Amazing New Medium
  * Code Notebooks let anyone write and run code in a browser.
  * With a narrative direction they are built for storytelling.
  * The notebook model lets you work from examples not write code. 
  * Try them free on [Google Colab](https://colab.research.google.com) (meh) or [AWS](https://studiolab.sagemaker.aws/) (better). 
  * [Geospatial Notebook Collection](https://notebooks.gishub.org) is a great way to learn A LOT, especially about Geospatial data.
* Your SQL skills are still valuable!  
  * Athena (sql/etc on - often free! - large data in cloud storage)
  * DuckDB (free multi-tool for small-medium data)
* Geospatial Tools
  * [QGIS](https://qgis.org) - Free and popular GIS
  * geojson.io and felt.com - look at and edit most geo data in a web page
  * export data from OSM or USGS - run queries and extractions
* Don't forget Google Spreadsheets & friends - Earth/Maps, etc
  * import CSV directly to process and visualize
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

* Just a spreadsheet and CSV
  * [Air/Water quality by region/city](https://www.kaggle.com/datasets/patricklford/water-and-air-quality)
  * Download, unzip, Import to a new Google Spreadsheet
  * Insert Chart > Geo (with Marker) > Select columns and options (set "address" to "Region")

* A vector data example: 
  * San Francisco Bay Area cares about Tsunamis!
  * Get somve vectordata [here](https://maps.conservation.ca.gov/cgs/informationwarehouse/ts_evacuation/)
  * and look at it with [geojson.io](geojson.io)
  
 
* A raster/CSV data example:
  * Global "risk" [data](https://data.humdata.org/dataset/econai-conflict-forecast)
  * [Notebook](https://internal.fireatlas.org:8888/notebooks/fellowship_demo.ipynb) with some basic Geospatial tools in place
  * Try adding another [data set](https://data.humdata.org/dataset/global-wfp-food-prices/resource/d62af4be-cff6-437b-89a3-67f8fa4c53bf)
  * or [Energy Access](https://www.kaggle.com/datasets/anshtanwar/global-data-on-sustainable-energy)

* Do some visualization
  * simple data here
  * empty notebook
  * use AI to build your visualization!
      
* Do some simple model building
  * similar 

Just wander:
* More advanced Climate Data [Colab notebook](https://colab.research.google.com/drive/16wQZgR29lfsV2RhGkuRvLNBc-hqByPVT?authuser=0)
* https://developers.google.com/earth-engine/datasets/catalog

Play:
* https://notebooks.gishub.org (start with "blog")
* https://felt.com
* https://www.epa.gov/enviroatlas/enviroatlas-dynamic-data-matrix
* https://colab.research.google.com/github/neuromatch/climate-course-content/blob/main/tutorials/W1D3_RemoteSensing/student/W1D3_Tutorial4.ipynb
      
