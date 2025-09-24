# fuelscape
(Climatebase Fellowship Capstone project)
A web-based tool to assess wildfire fuels reduction projects  - in particular, biochar production as part of

* *Main*: web based platform to gather geospatial data for a fuel reduction project and compare various ways to handle the carbon removed as fuel. In particular to estimate whether bio-char production can be used as a way to lower costs.

* *Secondary:* Platform for non-specialists to craft fuel reduction plans, generate needed documentation for funding and regulatory documents, and track progress and outcomes over time.

* *Teritary:* a "data narrative" (notebook) walking non-specialists through the process.


## Big Questions

### Current best practices for modeling fuel removal projects?
Duh - what else is out there already and can/should we just use that?

#### Requirements
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


## Initial Data and Models

### Treaments
Here are some qualitative sketches of different treatments to be modeled.

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




### Models
#### Simple (non-geospatial) Parameter Catalog
What are the basic parameters we need values for to build a "spreadsheet" model?
Some of these have to do with where a project might take place - let's assume that is external for now. That is, assuming a project will take place at a particular place and time, what do we need to assess very basic outputs like cost, carbon, etc. So we won't include:

##### Selection Criteria
* Typical scale / output 
* Seasons available
* Appropriate land types

##### Project Parameters - baseline daily cost

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


##### Implementaion Parameters - detail impacted, per acre
* acres treated/staff/day
* Cost
 * non-specialist staff
 * haulage
 * firesafe clearing and prep
* net carbon
* biochar generation
* fuel removal


#### A Really Bad Model
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




## Needed Contacts

* fuel reduction planners/implementors
* carbon markets startup/api/modeller
* biochar kiln producers and practitioners
* fuel reduction grant experts

## Architecture
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
 
    
## Use Cases
* Local VFD would like to explore adding bio-char generation to their existing process for fuel reduction in their local area.
* Community would like to put together a fuel reduction project, but don’t know the steps or have much budget to fund the work, let alone the preparation.
* Federate multiple projects
* track progress and outcomes over time

## Help Requested
* Carbon Markets
* Biochar Generation and Use
* Community Engagement
* Frontend Engineering
* Geospatial Modeling (fire and work in particular)
* Fuel Reduction grant writing and regulations
* Fire Department interfaces
* Cultural Burning and Native technologies
* grant writers and funding hunters
* fuel reduction and forestry practitioners

## Funding Model
A critical aspect of this project is that community fuel reduction projects are often short on funds. There is risk of paradox if it’s expensive to use the tool to make your projects less expensive.

### Free Service
Once the platform is built, there is little cost to running it - essentially, cloud hosting costs for a small service and datasets. A small grant or fundraising effort could likely pay for this well into the future. If it ran long enough and got enough use to run out of this initial funding, that would be a strong indicator that it was worth investing more effort and budget into.

### Small Community Grants
Many areas have block funding organizations or support for small local capacity improvement projects. In particular, “Technical Assistance” grants are intended for exactly this - generally minimal effort to apply for because they are small awards intended to help with the tooling and work needed to enable other programs and larger grant applications. So a community might get a TA grant to “bootstrap” a full fuel reduction project. A small one time fee for the service would fit very naturally into this TA structure, and by providing output that would facilitate making that larger fuel reduction project happen, would likely pay for itself.

Even small funding from the community and local organizations would likely be enough to fund access to the tool.

### SaaS 
It would be natural in some ways to seek startup funding and create a commercial service, likely with a larger or expanding set of features and use cases. Sliding scale pricing and/or non-profit status can help keep the service available to communities, but allow growth funded by commercial users with budget available.

## Open Questions
* how much of a general planning tool vs bio-char production modeling
* funding model
* one off vs ongoing
* how interactive
* data retention and access control
* sensitive data


## Plan

### Fellowship
* Week 2: approach and team
* Week 4: interviews and PoC model
* Week 6: parameters and candidate projects
* Week 8: web app, demo
  

### Post-Fellowship

