# Geom99 Group Project

In this log:

- [x] Project Overview (15/03/24 | 5 mins)
- [x] Finding Lindsay transit data (20/03/24 | 10 mins)
- [x] Uploading Lindsay transit data to ArcGIS Online (15/03/24 | 15 mins)
- [x] Exploring Public Transit Toolbox in ArcGIS Pro (20/03/24 | 30 mins)
- [x] Exploring Mapbox as a web solution (21/03/24 | 40 mins)
- [x] References

Total Duration: 90 mins

---

## Project Overview

**About the Project**

A group of four GIS students are exploring web solutions to find a user-friendly web application that will best help the general public navigate around Lindsay, Ontario, through public transportation.

**Lindsay Transit Map**

Kawartha Lakes. (2024). Lindsay transit. https://www.kawarthalakes.ca/en/living-here/resources/Transit/COKL-Transit-Map-2023.pdf 

**Four Routes**

- Orange (new as of Feb 2023)
- Green
- Red
- Blue

**Bus Schedule**

Kawartha Lakes. (2024). Lindsay transit. https://www.kawarthalakes.ca/en/living-here/lindsay-transit.aspx

---

## Finding Lindsay transit data

- One group member already acquired the data
- I did some more searching and found where the hub of real-time data is

### Transitland

URL: https://www.transit.land/feeds/f-kawartha~on~ca

#### About 

- stores the GTFS feed for Lindsay transit
- has current static data, but it is not up to date
	- this dataset is missing the orange transit line, which was added to the routes in Feb 2024
- have to make a free account to download the data
- nearly every day the feed is posted

> [!NOTE]
- I tried requesting an account to download the data, but received no confirmation email, so I am not able to sign in.
- We may have to continue with older data for the time being.

---

## Uploading Lindsay transit data to ArcGIS Online

Learn how to download public data from an ArcGIS Hub and upload it to ArcGIS Online as a hosted feature service

Assumption(s):
- User has an ArcGIS Account

Duration: 15 mins

### Steps

1. Visit the public **ArcGIS Hub** where Lindsay transit data are located: https://hub.arcgis.com/documents/ca68660b0e3e47a09a667d2f0963df99/about 

2. Browse the available data under **You may be interested in**.

3. Click ```Bus Routes``` feature service to bring you to an overview of its service.

4. Click ```Download``` to bring you to a list of **Download Options**.

5. In this case, we want the **Shapefile**. Find the shapefile on the list, click ```Download```. The zipfile including all shapefile data will automatically start downloading to the computer.

> [!IMPORTANT]
> Keep the folder zipped! ArcGIS Online will want you to upload a new item in a zipped file.

6. In a separate browser, sign into **ArcGIS Online**: https://www.arcgis.com/index.html# 

7. Once signed in, click ```Content```.

8. To keep files organized, on the lefthand side, click the ```folder icon``` next to **Folders** to create a new folder, where you will be storing the new items.

9. When in the folder, click ```New item``` at the top lefthand side of the page.

10. Drag and drop the zipped folder onto the page. AGOL will show that it is recognizes the uploaded folder was a **shapefile**.

11. We want the **zipped folder** AND the **hosted feature layer**, so select ```Add ___.zip and create a hosted feature layer```. Click ```Next```.

12. Give your shapefile a proper **name** and click ```Save```.

13. The shapefile will now appear in your AGOL with its associated hosted feature layer!

14. Repeat all steps for Lindsay's Bus Stops

:tada: *Congratulations! You have now learned how to upload the Lindsay, Ontario, transit data to ArcGIS Online*

> [!TIP]
> Click the hosted feature layer and view in Map Viewer to see the data on a map.

> [!WARNING]
> After further inspection of the data, it was discovered that some bus stops were missing. Further processing must be done to ensure the general public can rely on the data to navigate around the city.

---

## Exploring Public Transit Toolbox in ArcGIS Pro

Learn about the capabilities of the Public Transit Toolbox in ArcGIS Pro

Duration: 30 mins

### What is the Public Transit Toolbox?

- Toolbox in ArcGIS Pro that is used for displaying, converting, editing, and analyzing public transit data
- In this toolbox, there is an analysis toolset and a conversion toolset
	- analysis toolset used to analyze public transit data
	- conversion toolset used to convert to/from GTFS datasets

### Why is this toolbox of interest to our project?

- Since our group is working with public transit data, we decided to explore the tools within this toolbox
- We have GTFS Lindsay transit data, which can be processed using these tools

### GTFS to Public Transit Data Model

Learn how to use the **General Transit Feed Specification (GTFS) to Public Transit Data Model** tool to convert the GTFS data to a set of feature classes and tables that represent the transit data

Assumption(s):
- You have an ArcGIS Account with access to ArcGIS Pro and ArcGIS Online
- You already have the GTFS csv files downloaded

Duration: 30 mins

#### Steps

1. Open up a new project map in ArcGIS Pro. Save the project in a directory of your choice.

2. In the **Catalog Pane**:
    - Right click on ```Folders```
    - Click ```Add Folder Connection```
    - Navigate to the folder where your CSV files are saved on your local computer
	- Click ```OK```.
	- Expand the newly connected folder to see its contents

3. Once the folder connection is made, click the ```Analysis``` tab:
	- Click ```Environments```
	- Click the globe next to **Output Coordinate System**
	- Choose Coordinate System **NAD 1983 CSRS UTM ZONE 17N**
	- Click ```OK```

4. In the **Catalog Pane**:
	- Right click on your **geodatabase**
	- Click ```New```
	- Click ```Feature Dataset```
	- Ensure the **Output Geodatabase** is the one you’d like to store it in
	- Give the feature dataset a meaningful **name**
	- Ensure the **coordinate system** is the same one set in the environments
	- Click ```Run```

5. Click the ```Analysis``` tab 

6. Click ```Tools```

7. In the **Toolboxes** directory:
	- Click ```Public Transit Tools``` to expand the toolbox
	- Click ```Conversion``` to expand the toolset
	- Click ```GTFS to Public Transit Data Model```
	- This will bring up the **GTFS to Public Transit Data Model** Geoprocessing window

8. In the **Geoprocessing Window**:
	- For **Input GTFS Folders**, find the folder that olds your csv files
	- For **Target Feature Dataset**, choose the newly made feature dataset
	- Leave all other defaults
	- Click ```Run```

> [!NOTE]
> The target feature dataset chosen must not already have public transit data model feature classes within it.
> If the geodatabase being used is enterprise, it must not be versioned.

9. The feature classes and table will automatically be added to the map.

10. Explore the new data

| Item  | Type  | Location  | Description  |
| ------------- | ------------- | ------------- | ------------- |
| LineVariantElements  | Line  | Feature Dataset  | shows the route of the transit vehicle  |
| Stops  | Point  | Feature Dataset  | shows the bus stops  |
| CalendarExceptions  | Table  | Geodatabase  | ServiceID, ExceptionDate, ExceptionType |
| Calendars  | Table  | Geodatabase  | Empty; shows GServiceID, days of the week, StartDate and EndDate  |
| Lines  | Table  | Geodatabase  | shows 4 bus routes and route type  |
| LineVariants  | Table  | Geodatabase  | shows 4 bus routes; no direction data  |
| Runs  | Table  | Geodatabase  | TripID, CalendarID; wheelchair and bike columns null  |
| ScheduleElements  | Table  | Geodatabase  | ScheduleID and departure/arrivals |
| Schedules  | Table  | Geodatabase  | shows LineVarID  |

11. Suggestions for further exploration:

- Can schedule data be added to the tables?
- What type of calendar exceptions are they?
- Can we determine how long it will take to go from one stop to another?
- What other tools in the Public Transit toolbox might be useful for our project?

---

## Exploring Mapbox as an open source web solution

Learn the functionalities of Mapbox and explore it to see if it is a possible web solution to our group project

Duration: 40 mins

### What is Mapbox?

- Mapping and location platform for creating and customizing maps
- Uses APIs and SDKs
- Accounts are free, but many capabilities are not
- Used by many reputable companies (Snapchat, Foursquare, etc.)

### Why is this web solution of interest to our project?

- We need a web solution for our group project
- This web solution has a lot of open-source capabilities, which would make our project available to a wider audience
- Although the product is not free, they may be able to provide free licensing for student projects

### Why do people use Mapbox?

| Advantages  | Disadvantages  |
| ------------- | ------------- |
| The user interface has a "crisp look and feel"  | Many of the capabilities require coding  |
| Pricing is flexible, free tier to start  | There isn't documentation on everything  | 
| Super customizable, using API and SDK  | No ability for field data collection  |
| Augmented reality and storytelling options  | Not completely open source as people believe  |
| Has routing and geocoding processes  | Need to pay to use the services  | 
| Tutorials available to follow  |   |

GISGeography. (2024). Mapbox review: 5 things we like. https://gisgeography.com/mapbox/ 

### 'Getting started with Mapbox Standard in Studio' tutorial

Created a Mapbox account and completed the tutorial 'Getting started with Mapbox Standard in Studio,' which can be found here: https://docs.mapbox.com/help/tutorials/aa-standard-in-studio/

#### What did I do differently?

- Used different font (Poppins instead of Roboto Mono)
- Kept POI labels because I feel that if I were biking, I'd want to know the location of parks
- Removed the transit labels
- Used a different basemap (dusk instead of night)
- Used a different point color (yellow instead of purple)

#### What did I learn?

- Data was added from a GeoJSON file
- The Mapbox Standard interface is very simple and user-friendly
- Emission strength set to 1 means that the feature will appear the same regardless of the basemap style
- 'Slots' allow you to easily order your layers how you want them to appear
    - top: above POI, behind place and transit labels
    - middle: above lines, behind 3D buildings
    - bottom: above polygons
- When you zoom in and alter the direction of the north arrow, the buildings become three-dimensional 
- Publishing is really quick
- You and others can access each other's map styles, if made available to the public

#### Will this be a good web app for our project?

- It'd be neat to view the routes with the three dimensional buildings. This can make travelling easier, as you're able to locate landmarks as you go.
- Need to look more into the capabilities of the free version. Might not have full routing capabilities we are looking for.
- Not everyone in the group is comfortable with coding, so not sure if this is the best application to use.
- Not if we can't get free licensing for student projects.

#### Final product

![Final mapbox](/images/Mapbox/MapboxFinal.png)

---

## References

Esri. (2024). GTFS to public transit data model (public transit). *ArcGIS Pro.* https://pro.arcgis.com/en/pro-app/latest/tool-reference/public-transit/gtfs-to-public-transit-data-model.htm 

GISGeography. (2024). Mapbox review: 5 things we like. https://gisgeography.com/mapbox/ 

Kawartha Lakes. (2024a). Lindsay transit. https://www.kawarthalakes.ca/en/living-here/resources/Transit/COKL-Transit-Map-2023.pdf 

Kawartha Lakes. (2024b). Lindsay transit. https://www.kawarthalakes.ca/en/living-here/lindsay-transit.aspx

Private member. (2020). Lindsay transit map PDF. *ArcGIS Hub.* https://hub.arcgis.com/documents/ca68660b0e3e47a09a667d2f0963df99/about 