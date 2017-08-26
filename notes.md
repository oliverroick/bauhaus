# Notes

## 2017-07-22

### Experimenting with QGIS.

Here's an approach in QGIS that got me quite close to what I want. 

1. From a cities dataset, extract all places with more that 30000 residents. 
2. Buffer the cities based on their number of residents.
3. For each motorway, select the buffered polygons that intersect with the motorway, then select all cities inside these buffered polygons.
4. Create a large buffer around selected points and dissolve into one polygon.
5. Get the nodes from the polygon.
6. Create Voronoi polygons from the extracted nodes. 
6. Convert the polygons to lines.
7. Explode the lines into their segments.
8. Create a smaller buffer for the selected cities.
9. For each line segment, check whether both ending nodes are inside one of the buffer polygons; if not remove the segment from the dataset. 

## 2017-08-26

### Data preparation

I downloaded OpenStreetMap data from [Geofrabik's Data Extracts](http://download.geofabrik.de/index.html) for five federal states in Germany:

- Mecklenburg-Vorpommern
- Berlin/Brandenburg
- Sachsen-Anhalt
- Sachsen
- Thüringen

For each federal state, I extracted all roads  where `fclass=motorway` from `gis.osm_roads_free_1` and all places where `population>29999` from `gis.osm_places_free_1`. I then merged all five datasets for both roads and places into one dataset respectively and exported the result to GeoJSON. 




## Next

- Script this so that it can be run from the command line.
