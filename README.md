# ssci-591-project-3
**What this map shows:**
This map shows trails and restroom locations in and maintained by Santa Clara County Parks and Recreation. Santa Clara County is located in California, south of the San Francisco Bay. The purpose of this is to show trail users how accessible restrooms are near these trails.

**Starting sample:**
The starting sample for this project was Intro to FeatureLayer (https://developers.arcgis.com/javascript/latest/sample-code/intro-featurelayer/) from Esri's ArcGIS Maps SDK for JavaScript Sample Gallery. 

**What I changed:**

**Data source:**
Both data layers came from Santa Clara County Parks GIS Data Hub (https://gisdata-sccparks.hub.arcgis.com/).
The trail data is from a Dataset Feature Layer called "Santa Clara County Parks Trails" (https://gisdata-sccparks.hub.arcgis.com/datasets/SCCParks::santa-clara-county-parks-trails-1/about). This layer provides the trail locations and attributes displayed on the map and in the map pop-ups.
The restroom location data comes from the "Santa Clara County Parks Points of Interest" Dataset Feature Layer (https://gisdata-sccparks.hub.arcgis.com/datasets/SCCParks::santa-clara-county-parks-points-of-interest/about). Because the Points of Interest dataset contains many types of park features (such as campgrounds, trailheads, visitor centers, restrooms, etc.), I filtered it to display only restrooms, giving the map a focused and practical purpose. 
The map loads the trails from the Trails ArcGIS REST service (https://services1.arcgis.com/4QPaqCJqF1UIaPbN/arcgis/rest/services/Santa_Clara_County_Parks_Trails/FeatureServer/1) and the restroom locations from the Points of Interest ArcGIS REST service (https://services1.arcgis.com/4QPaqCJqF1UIaPbN/arcgis/rest/services/Point_of_Interests/FeatureServer/0). Both services are loaded using the ArcGIS Maps SDK for JavaScript FeatureLayer class. This allows the application to request the data from the county's online services whenever the map loads rather than storing static copies in the project.
I chose these datasets because I live in Santa Clara County and like to hike on many of these trails. They are maintained by the official Santa Clara County Parks GIS team and were updated in 2026, making them appropriate sources for a current informational map of county park trails and restroom locations.

**Component I added:**

**Problems and what I’d improve next:**

**Credits:**
