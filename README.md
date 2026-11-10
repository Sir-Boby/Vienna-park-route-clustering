# Vienna-park-route-clustering
GIS and machine-learning analysis of walking routes to urban green spaces in Vienna.
Vienna Park Route Clustering
Project Overview
This project develops a reproducible GIS and machine-learning workflow for analysing walking routes to urban green spaces in Vienna.

Walking routes from selected origin points to a park entrance are generated using the Vienna street network. Route-level environmental and network characteristics are then calculated in QGIS. Finally, K-Means clustering is used to group routes with similar characteristics.

Research Question
How can walking routes to an urban park be grouped based on their network and environmental characteristics?

Study Area
The pilot study focuses on one selected urban park and its surrounding area in Vienna, Austria.

Data
The project uses the following spatial datasets:

Vienna street network
Street network nodes
Public green spaces and park entrances
Strategic noise map, Lden
Tempo 30 zones
Additional environmental data may be added later
Large raw datasets are not stored in this repository. Their official sources and download links will be documented in the data/README.md file.

Project Workflow
1. Prepare the Spatial Data
The required spatial layers are imported into QGIS and checked for:

Geometry type
Coordinate reference system
Attribute structure
Missing or invalid geometries
All layers used for distance and area calculations are transformed to a suitable projected coordinate reference system.

2. Select the Park
One urban park is selected as the pilot destination.

The park polygon and its accessible entrance points are identified. One or more entrance points are used as destinations in the route analysis.

3. Create Origin Points
Origin points are generated around the selected park.

The origins may represent:

Residential building centroids
Regularly spaced sample points
Selected locations within the park service area
Each origin receives a unique identifier.

4. Generate Walking Routes
The shortest walking route from each origin to the selected park entrance is calculated using the Vienna street network.

Each resulting route receives a unique route_id.

5. Calculate Route-Level Features
The following features are calculated for each route:

Feature	Description
length_m	Total route length in metres
node_count	Number of street-network nodes along the route
intersection_count	Number of intersections along the route
noise_60plus_share	Proportion of route length exposed to at least 60 dB Lden
tempo30_share	Proportion of route length located within Tempo 30 zones
prd	Ratio between network distance and straight-line distance
Additional variables such as slope and tree-canopy exposure may be added later.

6. Export the Route Dataset
The route-level features are exported from QGIS as:

route_features.csv

