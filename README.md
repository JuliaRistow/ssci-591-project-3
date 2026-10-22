# ssci-591-project-3
## What this map shows: 

This map shows trails and restroom locations in and maintained by Santa Clara County Parks and Recreation. Santa Clara County is located in California, south of the San Francisco Bay. The purpose of this is to show trail users how accessible restrooms are near these trails.


## Starting sample: 

The starting sample for this project was Intro to FeatureLayer (https://developers.arcgis.com/javascript/latest/sample-code/intro-featurelayer/) from Esri's ArcGIS Maps SDK for JavaScript Sample Gallery. 


## What I changed: 

I changed the generic ArcGIS sample page title to "Santa Clara County Parks Trails and Restrooms" and styled the page to be visually aesthetic with customized colors, typography, spacing, and responsive behavior. 

I replaced the sample's tree carbon-storage layer with two Santa Clara County Parks feature layers (Trails and Points of Interest filtered to display restrooms). 

The basemap was changed from **hybrid** to **topo-vector**, and the sample's automatic tree-layer extent was replaced with a fixed center and zoom focused on Santa Clara County. 

I created a unique-value line renderer that distinguishes trails by route type. 

I originally planned to display multiple types of points of interest on the map, so I also created a unique-value point renderer. When I decided to only display restrooms, I kept this unique-value renderer to filter out the rest of the POI types. 

I replaced the sample's tree pop-up with a trail pop-up showing the park name, permitted uses, route type, length, difficulty, and status. I also added a restroom pop-up showing the park and restroom names. Although many restrooms are named "Restroom" or have no name, this field was included because some facilities have more specific and useful names. 

I added a page heading and an "About this map" description with links to both REST services. For the links, I created hyperlinks on the names of the data layers to keep the description easy to read, and I styled the hyperlinks to make the default, hover, and visited colors cohesive with the header. On small screens, the description is placed in a collapsible section so it remains available without permanently reducing the map area. 

I created buttons that filter trails by Easy, Moderate, or Strenuous difficulty. Very Easy trails are included with Easy trails, while Very Strenuous trails are included with Strenuous trails. The filter expressions account for differences in capitalization and use % as a wildcard to include "Very"; for example: **const EASY = "difficulty LIKE '%Easy' or difficulty LIKE '%easy'";**. The function **selectDifficulty** ensures that selecting a new filter deselects the previous one. A reset button removes the filter and restores all trails. A status message initially displays "Loading trails..." and then reports either the total number of trails or the number matching the active filter. There are more trails in the total count than the filtered amounts added together because some records in the dataset have Null values in the Difficulty field. The buttons change appearance when hovered over or selected and have a minimum size of 44 by 44 pixels to support touchscreen use.  

I also removed the sample's automatic zoom animation and navigation constraints.


## Data sources: 

Both datasets came from Santa Clara County Parks GIS Data Hub (https://gisdata-sccparks.hub.arcgis.com/). 

The trail data is from a Dataset Feature Layer called "Santa Clara County Parks Trails" (https://gisdata-sccparks.hub.arcgis.com/datasets/SCCParks::santa-clara-county-parks-trails-1/about). This layer provides the trail locations displayed on the map and the attributes in the map pop-ups. 

The restroom location data comes from the "Santa Clara County Parks Points of Interest" Dataset Feature Layer (https://gisdata-sccparks.hub.arcgis.com/datasets/SCCParks::santa-clara-county-parks-points-of-interest/about). Because this dataset contains many types of park features (such as campgrounds, trailheads, visitor centers, restrooms, etc.), I filtered it to display only restrooms, giving the map a focused and practical purpose. 

The map loads the trails from the Trails ArcGIS REST service (https://services1.arcgis.com/4QPaqCJqF1UIaPbN/arcgis/rest/services/Santa_Clara_County_Parks_Trails/FeatureServer/1) and the restroom locations from the Points of Interest ArcGIS REST service (https://services1.arcgis.com/4QPaqCJqF1UIaPbN/arcgis/rest/services/Point_of_Interests/FeatureServer/0). Both services are loaded using the ArcGIS Maps SDK for JavaScript FeatureLayer class. This allows the application to request the data from the county's online services whenever the map loads rather than storing static copies in the repository. 

I chose these datasets because I live in Santa Clara County and like to hike on many of these trails. They are maintained by the official Santa Clara County Parks GIS team and were updated in 2026, making them appropriate sources for a current informational map of county park trails and restroom locations.


## Components I added: 

I retained the Zoom, Layer List, and Legend components from the Sample but placed the Layer List and Legend inside expandable controls. Both begin collapsed on small screen devices. On large screen devices, the Legend begins expanded but can be collapsed by the user. The Layer List component was moved from the top right to the top left of the map. 

I added Home, Search, and Scale Bar components. Home returns the map to the initial center and zoom. Search allows users to search by park names and returns trails within the selected park.


## Problems and what I’d improve next: 

The problems I've noticed and haven't been able to fix are with the Search component. To search for a park, the user must begin typing the start of the name (for example: "Almaden Quicksilver") because searching with a word from the middle of the name, such as "Quicksilver", does not return a result. Also, searches do not always return every trail associated with a park. In this example, "Guadalupe Trail" is located in Almaden Quicksilver but does not appear in the search results. Some trails also appear multiple times in a search because the source dataset represents them as multiple line segments rather than a single continuous feature. For example, searching for "Los Gatos Creek" returns 6 results named "Percolation Pond Trail", with each result representing a different segment of the same trail. 

I want to fix these issues in a future version of this application so the Search component is more useful. 

I also want to expand the application by displaying additional types of points of interest, such as trailheads, parking areas, visitor centers, and campgrounds. To avoid overcrowding the map, I would also allow users to turn individual categories on and off through the Layer List, category buttons, or checkboxes. Each category could use a distinct symbol and appear in the Legend, allowing the application to provide more information while keeping the display understandable and focused on each user's needs. 


## Credits:

*Data:* 

Santa Clara County Parks and Recreation (2026). Santa Clara County Parks Points of Interest (dataset). Santa Clara County Parks GIS. https://gisdata-sccparks.hub.arcgis.com/datasets/SCCParks::santa-clara-county-parks-points-of-interest/about
Santa Clara County Parks and Recreation (2026). Santa Clara County Parks Trails (dataset). Santa Clara County Parks GIS. https://gisdata-sccparks.hub.arcgis.com/datasets/SCCParks::santa-clara-county-parks-trails-1/about

*Sample Code:*

ArcGIS Maps SDK for JavaScript // Sample Code. Intro to FeatureLayer (Sample Code). Esri Developers. https://developers.arcgis.com/javascript/latest/sample-code/intro-featurelayer/

*Additional References:* 

ArcGIS Maps SDK for JavaScript // References. arcgis-scale-bar (Reference). Esri Developers. https://developers.arcgis.com/javascript/latest/references/map-components/components/arcgis-scale-bar/
ArcGIS Maps SDK for JavaScript // References. SimpleLineSymbol (Reference). Esri Developers. https://developers.arcgis.com/javascript/latest/references/core/symbols/SimpleLineSymbol/
ArcGIS Maps SDK for JavaScript // References. UniqueValueRenderer (Reference). Esri Developers. https://developers.arcgis.com/javascript/latest/references/core/renderers/UniqueValueRenderer/
ChatGPT, responses to questions about debugging HTML and JavaScript code. OpenAI. http://chatgpt.com
HTML Links. W3Schools. https://www.w3schools.com/html/html_links.asp
HTML Links - Different Colors. W3Schools. https://www.w3schools.com/html/html_links_colors.asp
