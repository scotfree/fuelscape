# Tool to assess biochar production in community wildfire fuels reduction projects
*Climatebase Fellowship Capstone project*

* *Main*: web based platform to gather geospatial data for a fuel reduction project and compare various ways to handle the carbon removed as fuel. In particular to estimate whether bio-char production can be used as a way to lower costs or increase benefits.

* *Secondary:* Platform for non-specialists to craft fuel reduction plans, generate needed documentation for funding and regulatory documents, and track progress and outcomes over time.

* *Tertiary:* a "data narrative" (notebook) walking non-specialists through the process.

# Overview

Wildfire-threatened communities across the West know they need to reduce fuels - but turning this knowledge into plans and action is another story. Projects are expensive, logistics are messy, and navigating grants can be overwhelming for small fire safe councils and local volunteer departments. Meanwhile, every year of delay means more fuel in the forest, higher wildfire risk, and more carbon released into the atmosphere when fires inevitably burn.Even when funding is available - like existing RFPs for biochar kilns or proposals for “lending libraries” - local groups often lack the tools to explore these options. 

Our goal here is to give communities a way to model wildfire fuel reduction projects and explore whether biochar production could strengthen them. We’ll do this by providing a simple, geospatial web platform designed for local needs and fully compatible with tools they may already use.Within that platform, users can model different treatment approaches - taking into account geography, ecology, staffing, implementation rules, and importantly: budget. The results will be easy to export in formats they can use for grant applications, regulatory filings, and project planning.Finally, we’ll model how integrating biochar production could offset costs, simplify logistics, and unlock new sources of funding through carbon markets - turning what is now a daunting idea into a clear, actionable opportunity.

    
## Use Cases
* Local VFD would like to explore adding bio-char generation to their existing process for fuel reduction in their local area.
* Community would like to put together a fuel reduction project, but don’t know the steps or have much budget to fund the work, let alone the preparation.
* Federate multiple projects
* track progress and outcomes over time

## Product System
* *Platform:* web app - interactive maps and upload of geospatial/planning documents
* *Input:* Potential Wildfire Fuel Reduction (WFR) Plan (treatment location, areas, methods, staff/timeline)
* *Model:* treatment plan -> biomass extracted -> biomass processed -> (biochar produced) -> cost / impact
* *Outputs:*
    * core metrics: cost, net carbon, seasonal and other restrictions
    * artifacts: grant content, spreadsheet
    * planning hints - schedule orchestration, equipment, etc

## Needed Conversations / Contributors
* fuel reduction planners/implementors
* carbon markets startup/api/modeller
* biochar production
* grant writing and funding
* Community Engagement - local organizations (fire dep'ts, tribes, fire safe councils, RCDs, NGOs, etc)
* Frontend Engineering - maplibre, fastAPI, sedona/spark, duckdb/pg
* Geospatial platforms and Modeling (fire and logistics in particular)
* Cultural fire and TEK


## Funding Models
A critical aspect of this project is that community fuel reduction projects are often short on funds. There is risk of paradox if it’s expensive to use the tool to make these projects less expensive.

### Free Service
Once the platform is built, there is little cost to running it - essentially, cloud hosting costs for a small service and datasets. A small grant or fundraising effort could likely pay for this well into the future. If it ran long enough and got enough use to run out of this initial funding, that would be a strong indicator that it was worth investing more effort and budget into.

### Small Community Grants
Even small funding from the community and local organizations would likely be enough to fund ongoing access to the tool.

Many areas have block funding organizations or support for small local capacity improvement projects. In particular, “Technical Assistance” grants are intended for exactly this - generally minimal effort to apply for because they are small awards intended to help with the tooling and work needed to enable other programs and larger grant applications. So a community might get a TA grant to “bootstrap” a full fuel reduction project. A small one time fee for the service would fit very naturally into this TA structure, and by providing output that would facilitate making that larger fuel reduction project happen, would likely pay for itself.


### SaaS 
It would be natural in some ways to seek startup funding and create a commercial service, likely with a larger or expanding set of features and use cases. Sliding scale pricing and/or non-profit status can help keep the service available to communities, but allow growth funded by commercial users with budget available.


# Data and Models

## Treaments
Here are some qualitative sketches of different treatments to be modeled. We've made wild attempts to quantify these and put them in more easily used (JSON) format [here](../parameters.json). Refining these numerical values is likely a core part of the work to be done - but note that we may care much more about relative than absolute values. Our core goal is to help rank different treatments, not perfectly estimate their costs.

| Treatment (examples)                                |   Typical scale / output |        Cost (per acre) | Staff required | Expertise required |     Equipment required | Seasons available | Firefighter supervision needed? | Appropriate land types                        |                    Carbon impact (relative) | **Biochar Potential**                                    | Notes                                                     |
| --------------------------------------------------- | -----------------------: | ---------------------: | -------------: | -----------------: | ---------------------: | ----------------: | ------------------------------: | --------------------------------------------- | ------------------------------------------: | -------------------------------------------------------- | --------------------------------------------------------- |
| Hand thinning & limbing (cut & scatter)             |   Small lots; low volume |             Low–Medium |     Low–Medium |         Low–Medium |  Chainsaws, hand tools |        Year-round |                              No | Steep slopes, around homes, sensitive terrain |                                Low–Moderate | **Low** (if slash later charred in kiln)                 | Biomass remains; could be moved to biochar kiln later.    |
| Hand thinning + piling (for later treat)            |         Small properties |             Low–Medium |         Medium |         Low–Medium |         Same + winches |        Year-round |     If piles burned later – Yes | Steep, close to structures                    | Variable (if piles burned → high emissions) | **Medium** (if piles processed via biochar kiln)         | Good prep step for later biochar conversion.              |
| Chipper — small walk-behind / homeowner (≤3–4" dia) |     Small volumes, brush |                    Low |            Low |                Low |          Small chipper |        Year-round |                              No | Yards, small parcels                          |                                Low–Moderate | **Low** (chips could be used as feedstock)               | Chips are good feedstock for pyrolysis units.             |
| Chipper — towable / truck-mounted (4–8" dia)        | Medium parcels, roadside |                 Medium |         Medium |             Medium | Towable chipper, truck |        Year-round |                      Usually no | Roadsides, fuel breaks                        |                                Low–Moderate | **Medium** (bulk chip supply for biochar plant)          | Can feed larger biochar/biomass energy operations.        |
| Chipper — large industrial / tub grinder (>8"+)     |              High volume |                   High |           High |               High |   Tub grinder, loaders |        Year-round |                              No | Forest stands, biomass                        |                                    Moderate | **High** (bulk chip feedstock for continuous pyrolysis)  | Good for industrial biochar or biomass energy markets.    |
| Mastication / masticator (tractor-mounted)          |           Large acreages |            Medium–High |     Low–Medium |             Medium |             Masticator | Non-windy seasons |                       Sometimes | Chaparral, shrublands                         |                                Low–Moderate | **Low** (mulch can be later collected but rarely is)     | Usually leaves biomass as mulch, not charred.             |
| Mechanical (cut-to-length) & removal                |             Timber-scale |                   High |           High |               High |   Harvesters, skidders |          Seasonal |                     Not usually | Timberlands                                   |                                    Variable | **Medium** (slash can be processed to char if recovered) | Primary output is logs; slash may be used for biochar.    |
| Lop-and-scatter                                     |             Small–medium |                    Low |     Low–Medium |                Low |              Chainsaws |        Year-round |                              No | Near homes                                    |                                    Moderate | **Low**                                                  | Leaves biomass to decompose.                              |
| Pile burning (burning hand-created piles)           |              Small piles |                    Low |     Low–Medium |             Medium |      Hand tools, pumps |   Wet/cool season |                         **Yes** | Close to homes, steep slopes                  |                                        High | **Very Low** (nearly all carbon lost)                    | Produces ash, not biochar.                                |
| Broadcast prescribed fire                           |          Landscape-scale |             Low–Medium |    Medium–High |               High |       Engines, torches |  Specific windows |                         **Yes** | Fire-adapted forests                          |                                    Moderate | **Very Low** (most carbon combusted)                     | Leaves minimal char; primarily an emissions source.       |
| Pile burning w/ air-curtain incinerator             | Concentrated high volume |                 Medium |         Medium |             Medium |     Air-curtain burner |        Year-round |                       Sometimes | Large clearings                               |                               Moderate–High | **Low–Medium** (some char left if not over-burned)       | Most carbon combusted but can leave some char residue.    |
| Air curtain for biochar feedstock (char capture)    |             Small–medium |            Medium–High |         Medium |        Medium–High |       Specialized unit |          Flexible |                        Possible | Community fuel sites                          |                                    Variable | **High**                                                 | Designed to retain char for soil use.                     |
| Biochar — TLUD / top-lit updraft                    |            Small batches |             Low–Medium |            Low |         Low–Medium |             TLUD kilns |        Year-round |                      Usually no | Small plots                                   |                            **Net-negative** | **High**                                                 | Simple way to convert slash to stable char.               |
| Biochar — retort / batch kilns                      |     Farm/community scale |                 Medium |         Medium |             Medium |           Retort kilns |          Seasonal |                        Possibly | Farms                                         |                            **Net-negative** | **High**                                                 | Higher efficiency & char yield than open burns.           |
| Biochar — continuous pyrolysis (mobile plant)       |               Industrial |             High capex |           High |               High |  Mobile pyrolysis unit |        Year-round |                              No | Large biomass sites                           |                            **Net-negative** | **Very High**                                            | Produces large volumes of char + usable energy.           |
| Chipping + hauling offsite (to mill, energy plant)  |                 Variable |            Medium–High |    Medium–High |             Medium |       Chippers, trucks |        Year-round |                              No | Accessible forest                             |                                    Variable | **Medium–High** (if feedstock sent to biochar facility)  | Biochar potential depends on end-market.                  |
| Grinding & pelletizing / biomass energy             |               Industrial |                   High |           High |               High |  Grinders, pelletizers |        Year-round |                              No | Near biomass plants                           |                                    Variable | **Medium** (if co-located with char-producing plant)     | Most biomass energy plants combust fully — low char left. |
| Prescribed/targeted grazing                         |             Small–medium |             Low–Medium |     Low–Medium |         Low–Medium |           Fence, water |          Seasonal |                              No | Grasslands, shrublands                        |                                         Low | **None**                                                 | No char produced.                                         |
| Herbicide treatment                                 |                 Targeted |             Low–Medium |            Low |             Medium |             Spray gear |          Seasonal |                              No | Targeted invasives                            |                                    Variable | **None**                                                 | Biomass usually left in place to decompose.               |
| Wildfire fuelbreak construction                     |      Landscape corridors |                   High |           High |               High |    Dozers, masticators |   Off fire season |       Yes (if near fire season) | Strategic corridors                           |                                    Variable | **Low**                                                  | Biomass may be burned or mulched; rarely charred.         |
| Merchantable thinning / selective harvest           |             Timber-scale | Often revenue-positive |           High |               High |        Logging systems |          Seasonal |                              No | Productive forests                            |                             Potentially low | **Medium** (slash can be charred)                        | Depends if slash recovery for char is prioritized.        |




## Models
### Simple (non-geospatial) Parameter Catalog
What are the basic parameters we need values for to build a "spreadsheet" model?
Some of these have to do with where a project might take place - let's assume that is external for now. That is, assuming a project will take place at a particular place and time, what do we need to assess very basic outputs like cost, carbon, etc. So we won't include:

#### Selection Criteria
* Typical scale / output 
* Seasons available
* Appropriate land types

#### Project Parameters - baseline daily cost

* total acres
* staff size
* project managers
* Expertise/Specialists required
 * firefighter overwatch
 * foresters
 * equipment operators
 * biologists
* Equipment required
 * fuel transportation
 * towables
 * deployment vehicls
 * hand gear


#### Implementaion Parameters - detail impacted, per acre
* acres treated/staff/day
* Cost
 * non-specialist staff
 * haulage
 * firesafe clearing and prep
* net carbon
* biochar generation
* fuel removal


### A Really Bad Model
Let's make a ton of horrible assumptions and invalid oversimplifications then use them in s really bad model!

```
inputs = [acres, staff]
days = ceiling( acres / (staff * speed) )
daily_cost = crew + staff + equipment + transportation

```
Want
* hauling impact even if not geographic - low density vs high density treatment areas
* transportation scaled to actual produced waste.
* So fuel removed becomes waste at some ratio



### ChatGPT's Bad Model
Asking AI for some basic summarization and simple modeling provides another sketch:

```
Simple quantitative models for wildfire fuel reduction costs are generally statistical, based on factors like treatment type, location, topography, and project size. The most straightforward approach is using average cost-per-acre data, but more sophisticated models incorporate multiple variables to improve accuracy. [1, 2, 3, 4]  
Cost-per-acre average The simplest model is to use an average cost-per-acre. This can provide a very rough, back-of-the-envelope estimate but does not account for site-specific variability. 
Formula 
Where: 

•  = Total estimated project cost 
•  = Area to be treated in acres 
•  = Average cost per acre for a specific treatment type [5, 6]  

Example: For a 500-acre project using prescribed fire, if the average cost for that method is $170 per acre, the estimated cost is . [1]  
Limitations: This model is unreliable because costs can vary significantly based on factors like slope, proximity to development, and fuel type. [7, 8]  
Regression-based models Regression models account for multiple variables and are used by agencies like the USDA Forest Service to produce more reliable cost estimates. Separate models are often developed for different treatment types, such as prescribed burning and mechanical thinning. [1, 2, 9, 10]  
Factors included in regression models Factors commonly used in these models include: 

• Treatment type: Prescribed burning vs. mechanical thinning. Prescribed fire is often less expensive per acre. 
• Project size (acres): Increasing the treated area often results in a lower cost per acre due to economies of scale. 
• Wildland-Urban Interface (WUI): Costs are often higher in or near the WUI due to more intensive safety precautions and higher labor costs. 
• Topography: Projects on steep slopes or rugged terrain cost more due to reduced accessibility for machinery. 
• Proximity to populated areas: Treating land closer to urban areas increases costs due to liability and logistical challenges. 
• Fuel characteristics: Different fuel types and densities affect the time and resources needed for treatment. [1, 2, 11, 12, 13]  

Formula (generalized) A typical regression model for cost might look like this: 

Where: 

•  = Estimated cost per acre 
•  = The model's intercept (base cost) 
•  = Number of acres in the project (can have a negative coefficient due to economies of scale) 
•  = Indicator variable (1 if project is in WUI, 0 otherwise) 
•  = Average slope of the project area 
•  = Average elevation of the project area 
•  = Error term 
•  = Regression coefficients that define the effect of each variable on cost [1, 2, 12, 14, 15]  

How it works: 

1. Data collection: The model is built by analyzing historical cost data from past projects, like the Forest Service Activities Tracking System (FACTS). 
2. Fitting the model: Statistical software uses this data to find the best-fit coefficients ( values) for each variable. 
3. Prediction: A user enters the characteristics of a new project, and the model calculates the estimated cost per acre. The total cost is found by multiplying this result by the project size. [2, 16]  

Advanced spreadsheet models The US Forest Service and other researchers have developed spreadsheet-based models that use regression equations to provide practical tools for fire managers. For example, the Forest Service has a model that allows users to input up to three treatment types, the geographic region, county, and acres to estimate costs. [2, 5, 14]  
Factors beyond simple models While the models above capture key quantitative aspects, other qualitative and highly variable factors can impact costs, such as: 

• Permitting and planning costs: Developing burn plans, completing environmental assessments, and obtaining permits can be costly. 
• Weather dependency: Prescribed burns depend heavily on weather windows, and delays can increase overall project costs. 
• Site-specific hazards: Difficult access, sensitive habitat, or the presence of specific tree species can add complexity and cost. [17, 18, 19]  

AI responses may include mistakes.

[1] https://www.rff.org/documents/4746/WP_25-03.pdf
[2] https://www.fs.usda.gov/psw/publications/documents/psw_gtr261en/psw_gtr261_085.pdf
[3] https://www.swfireconsortium.org/wp-content/uploads/2016/12/Econ_Final_Web-2.pdf
[4] https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0319787
[5] https://research.fs.usda.gov/treesearch/57676
[6] https://www.fs.usda.gov/rm/pubs_journals/2023/rmrs_2023_chang_h001.pdf
[7] https://www.publish.csiro.au/wf/Fulltext/WF23182
[8] https://plumassun.org/2025/09/21/unburned/
[9] https://fireecology.springeropen.com/articles/10.1186/s42408-022-00159-y
[10] https://www.publish.csiro.au/wf/fulltext/wf14058
[11] https://agrilife.org/westtexasrangelands/analysis-of-the-cost-and-cost-components-of-conducting-prescribed-fires-in-the-great-plains/
[12] https://eri.nau.edu/science-flash-january-2023-determining-forest-thinning-operation-costs/
[13] https://www.sciencedirect.com/science/article/pii/S0378112721007647
[14] https://research.fs.usda.gov/treesearch/57676
[15] https://onlinelibrary.wiley.com/doi/10.1002/ldr.5652
[16] https://www.emerald.com/ecam/article/29/7/2836/34824/Application-of-stacking-ensemble-machine-learning
[17] https://ucanr.edu/sites/default/files/2020-04/324837.pdf
[18] https://www.sciencedirect.com/science/article/pii/S2949790624002003
[19] https://bioone.org/journals/rangeland-ecology-and-management/volume-92/issue-1/j.rama.2023.11.002/Analysis-of-the-Cost-and-Cost-Components-of-Conducting-Prescribed/10.1016/j.rama.2023.11.002.full



```



# Technical Implementation
* cloud service - serverless
* cheap slow cloud storage
* simple universal formats for interoperability
  * geojson
  * COG
* Web interface for model parameters (as JSON)  and runs
* input:
  * geojson layers for fuel, vegetation, transport, etc
  * geojson or direct drawing interface for treatment areas
  * geojson, drawn, or (stretch goal!) predicted gathering points
  * biome, season, climate parameters
* output:
  * map layers
  * grant proposal components
  * spreadsheet comparing treatments
 

# Open Questions
## General Product Questions
* how much of a general planning tool vs bio-char production modeling
* funding model
* one off vs ongoing
* how interactive
* data retention and access control
* sensitive data

## Big Questions
### Current best practices for modeling fuel removal projects?
What else is out there already and can/should we just use that?

Thus far there doesn't seem to be a widely used general approach here. There are a few papers suggesting them or summarizing results. IN particular, a [Forest Service](https://www.fs.usda.gov/psw/publications/documents/psw_gtr261en/psw_gtr261_085.pdf) mentions a "Spreadsheet Model" for fuel reduction cost estimation - however, I have not yet been able to find a version of it. 

The standard approaches seem to largely be simple models run to simple area based approaches. There's a quick ChatGPT take on this below, but essentially they mostly set a per-acre cost for broad treatment types, then modify this with large location features: North vs South half of California, for example - or critically, whether the treatment area is in the Wildland Urban Interface (WUI). These are great places to start and we need to agree with these models or justify where we differ. 

They do seem to lack some general properties which may justify the need for the Fuelscape tool:
* don't address carbon impacts in general - this may be useful for certain grant and funding structures, beyond local desire for "green" projects
* don't express biochar production specifically - impact not only on carbon but other modeled aspects: cost, risk, staff, etc.
* take an existing plan and predict cost - not a way to make a plan and help get it deployed

These "product" observations lead to some "technical" preferences:

### Requirements
* open source free software
* able to incorprate/ignore  parameters in catalog
* output as numbers and ideally richly formatted text/document



### How important is geometry?
I want to model the fuel reduction treatment explicitly, with fuel distributed geographically and explicit treatment points. I must admit however that partly that just SOUNDS REALLY FUN. I want to path workers and trucks across terrain and have placement of kilns relative to fuel sources matter. That doesn't mean it's very meaningful though.

It may just be that the various rankings and efficacies of treatment methods is realtively constant and the choices are just made based on various availabilities. Even in that case though, it might be useful to model explicitly to get cost estimats for Goal 2.

So: How much does the geospatial detail of the treatment plan and its context impact the options?

Guessed parameters:
* scale - if we're clearing a whole forest, the details may not matter
* fuel type - some forms of wood may be more costly to move
* seasonality - during less safe seasons, there may be impacts on number/placement of burn sites
* treatment method - for a gang of people with hand tools doing chop-and-scatter, it may not matter much how the fuel is layed out.

### Is selling produced biochar on carbon markets a thing?
It's the idea which triggered some of this but still largely unquantified! If we produce X amount of biochar how much budget does that translate to?

Obviously there are a lot of variables we need to know to answer this, but let's find out what they are and start estimating! Let's assume the cost of biochar production is handled elsewhere, since (we think) that's very dependent on the treatment chosen. 

Guessed Parameters:
* state of carbon market (is this a simple price per ton or what?)
* logistics overhead: do we pay to get the biochar somewhere - on a truck, in the soil, whatever
* quantity and regularity of production
* grade?

### What is the input?

There are at least two parts to this: we need to know where the fuels are and then how the project intends to remove them.

#### Where does fuel data come from?
Ideally, customers come with existing data about the fuels distribution in their project area.
When this is not the case, or the data isn't rich enough, we have a few options.

* public fuels data - there may be public data available
 * availability - is data available at all?
 * scale/accuracy - is data too coarse grained or inaccurate or dated to be useful, or used unprocessed.
* photogrammetry and lidar can be used to estimates geographical distribution of fuels. Getting accurate data on things like ladder fuels and tree hights in addition to species or type is possible, but depends on input data and depth of analysis we're willing to apply.
* drone video and analysis can provide remarkably detailed models of individual tree, species, and carbon. This can be generated with commodity drones but requires fairly sophisticated analysis - generally gaussian splatting these days.


#### Where does treatment/project data come from?
Can we assume communities wanting to do fuel reduction come with geospatial data about the fuel locations and context?
Probably not.
So, do they draw it in our app? 
Do they describe it verbally as an LLM prompt which we turn into SQL and Geojson then display back to them so they can edit and tune it using web based map tools? I mean: yes. That sounds very cool.

* upload and process customer provided plan data
* draw directly as polygon geometries in app
* apply LLM prompt -> SQL -> geometries
* automagically approximate
* suggest plans based on various criterion - likely not only cost


# Plan

## Fellowship
* Week 2: approach and team
 * summarize competition
 *  find interested people with relevant experience/skills
 *  stretch: horrible draft model
* Week 4: interviews and PoC model
 * interview - WFR
 * interview - biochar
 * interview - carbon market
 * basic non-geometry model
 * identify potential user(s)
* Week 6: parameters and candidate projects
 * compare to published results, models, data
 * import existing WFR plan (spreadsheet and/or geoJSON)
 * improved model
 * basic geometric model
 * interview - grant funding
 * interview potential user
* Week 8: web app, demo
 * compare geometric to non
 * create model in app
 * grant/doc output format 
 * release open source

## Post-Fellowship
* pursue grants

# Reading and Links
## Policy and Overview
* https://research.fs.usda.gov/treesearch/67944 General Technical Report
* https://click.news.fs.usda.gov/?qs=85917c983f4fbcf6f862300e64941625c60ef8418cb596c6f2ca82e454344b214554ea42c0e42b6fe94e5ac6af1b93700ea637436a69f175835853cf820b6f8b SYCU
* https://permitsonoma.org/hazfuelsreduction
* https://research.fs.usda.gov/treesearch/57676
* https://www.doi.gov/wildlandfire/fuels
* https://research.fs.usda.gov/psw/projects/alternative-treatments-wildland-urban-interface
* https://research.fs.usda.gov/treesearch/64794 BioChar primer SYCU


## Quantitative Modeling
* https://www.mdpi.com/2571-6255/6/3/104  A Quantitative Analysis of Fuel Break Effectiveness Drivers in Southern California National Forests
* https://fireecology.springeropen.com/articles/10.1186/s42408-022-00157-0 A framework for quantifying forest wildfire hazard and fuel treatment effectiveness from stands to landscapes
* https://research.fs.usda.gov/treesearch/57676 Wildfire fuel reduction cost analysis: Statistical modeling and user model for fire specialists in California
* https://www.rff.org/news/press-releases/new-study-identifies-costs-of-wildfire-fuel-treatment-in-california/#:~:text=Treating%20areas%20with%20high%20wildfire,and%20San%20Bernardino%20mountain%20ranges. New Study Identifies Costs of Wildfire Fuel Treatment in California
* https://www.rff.org/publications/working-papers/the-costs-of-achieving-forest-resilience-in-california/  The Costs of Achieving Forest Resilience in California
  
## Companies and Consultancies and Apps and Games
* https://pyrologix.com/solutions/
* https://research.fs.usda.gov/rmrs/products/dataandtools/pyrotown-serious-educational-game-integrated-fire-management-students pyrotown
* 
