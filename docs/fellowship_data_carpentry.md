class: top-bottom-slide
background-image: url(vis_globalvapor.jpg) 
# Empower Yourself With Data!
See something cool, learn how much is available and open, share a tip.
Get in touch!
 
* http://fuelscape.net/fellowship_data_carpentry.html#1
* https://github.com/scotfree/fuelscape/  
* gateless@gmail.com
* https://www.linkedin.com/in/scot-kennedy-7a04265/
* Scot Kennedy  
  
---
class: top-bottom-slide
background-image: url(vis_radar.png)    
# Overview of Session



* Interesting and **Open** Data
* Useful and **Open** Tools
* **Opening** PandorAI's Box
* **Open** Horizon
  
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
# Types, Formats, and Tips
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
    * "Dataframes" are like spreadsheets with lots of code attached and no built-in interface, widely usable in python and apps.
   
---
class: top-bottom-slide
background-image: url(vis_sankey.png) 
# environmental and societal
  * https://data.humdata.org
  * https://jeiloh.github.io/esip_dlc_trusted_data/
  * [NASA](data.nasa.gov) hosts an incredible variety of climate-relevant datasets.
  * [UN Food & Ag](https://www.fao.org/faostat/en/#data) has an amazing range of global datasets.
   
---
class: top-bottom-slide
background-image: url(vis_states.png) 
# Maps and Geospatial Data 
  * Open Street Map
    * [Simple Maps](https://www.openstreetmap.org/search?query=rare+earth+mine&zoom=9&minlon=-117.60864257812501&minlat=34.30260622622907&maxlon=-113.40362548828126&maxlat=36.41686211530033#map=17/35.503225/-115.511230)
    * [Turbo and Overpass](https://overpass-turbo.eu)
  * [Overture](https://explore.overturemaps.org/#5.41/40.336/-74.488)
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
* Don't forget Google Spreadsheets & friends - Earth/Maps, etc
  * import CSV directly to process and visualize
  * spreadsheet linked to map
* Your SQL skills are still valuable!  
  * Athena (sql/etc on large data in cloud storage -  [Overture](https://docs.overturemaps.org/getting-data/) etc)
  * DuckDB (free "multi-tool" for small-medium data) - [Home](https://duckdb.org) 
* Geospatial Tools
  * [QGIS](https://qgis.org) - Free and popular GIS
  * [geojson.io](geojson.io) and [Felt](felt.com) - look at and edit most geo data in a web page
  * export data from OSM or USGS - check your local government! {Humboldt County Web GIS](https://cty-gis-web.co.humboldt.ca.us/HCEGIS3.0/)
* Put some data in AWS S3 and be amazed! There's an analysis ecosystem already pointed at it!

---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
# Notebooks!
* Code Notebooks let anyone write and run code in a browser.
* Work from examples not write code. 
* With a narrative direction, graphics, and typesetting they are built for storytelling. [Matrix Math](https://nbviewer.org/github/sdrelton/matrix_function_notebooks/blob/master/TheMatrixExponential.ipynb)
* Try them free on [Google Colab](https://colab.research.google.com) (meh) or [AWS](https://studiolab.sagemaker.aws/) (better). 
* [Geospatial Notebook Collection](https://notebooks.gishub.org) is a great way to learn A LOT, especially about Geospatial data.
* [More examples](https://gist.github.com/ocoyawale/54d92fd4bf92508a2a6e482b5fa480fd#mathematics)

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
* A raster/CSV data example:
  * Global "risk" [data](https://data.humdata.org/dataset/econai-conflict-forecast)
  * [Notebook](https://internal.fireatlas.org:8888/notebooks/fellowship_demo.ipynb) with some basic Geospatial tools in place
  * Try adding another [data set](https://data.humdata.org/dataset/global-wfp-food-prices/resource/d62af4be-cff6-437b-89a3-67f8fa4c53bf)
  * or [Energy Access](https://www.kaggle.com/datasets/anshtanwar/global-data-on-sustainable-energy)

---
class: top-bottom-slide
background-image: url(minkin-multicolor1.png) 
# (more) Open Horizons and Examples
* A vector data example: 
  * San Francisco Bay Area cares about Tsunamis!
  * Get somve vectordata [here](https://maps.conservation.ca.gov/cgs/informationwarehouse/ts_evacuation/)
  * and look at it with [geojson.io](geojson.io)
* Do some visualization and modelbuilding!
  * simple data here
  * empty notebook
  * use AI to build your visualization!

---
class: top-bottom-slide
background-image: url(vis_radar.png)  
# Just wander around and play with stuff!
*More advanced Climate Data [Colab notebook](https://colab.research.google.com/drive/16wQZgR29lfsV2RhGkuRvLNBc-hqByPVT?authuser=0)
* https://developers.google.com/earth-engine/datasets/catalog
* https://notebooks.gishub.org (start with "blog")
* https://felt.com
* https://www.epa.gov/enviroatlas/enviroatlas-dynamic-data-matrix
* https://colab.research.google.com/github/neuromatch/climate-course-content/blob/main/tutorials/W1D3_RemoteSensing/student/W1D3_Tutorial4.ipynb
      
