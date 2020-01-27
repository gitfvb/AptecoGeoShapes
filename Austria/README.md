
# Verwaltungsgrenzen

## Source

* Verwaltungsgrenzen: http://data.opendataportal.at/dataset/geojson-daten-osterreich

# Postleitzahl

## Source

* OpenStreetMap via OverpassTurbo
* Query: 

```javascript
/* all postal codes in Austria */
area["name:en"="Austria"][boundary=administrative]->.myarea;
rel(area.myarea)[postal_area~".*"];
/*added by auto repair*/
(._;>;);
/*end of auto repair*/
out;
```

## Further steps to use the shapes

### Challenges

* Create the map for the five digit postcode beforehands
* 

### Steps

1. Open OverpassTurbo and use the query
2. Download the data and open it in QGIS

