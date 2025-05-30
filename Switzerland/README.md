# Swiss Boundaries

https://www.swisstopo.admin.ch/de/geodata/landscape/boundaries3d.html#technische_details

# Amtliches Ortschaftenverzeichnis

## Source

* https://www.cadastre.ch/de/services/service/registry/plz.html

## Results

* 2 and 4 digit postal code map
* Gemeinden
* Grossregionen
* Kantone

## Further steps to use the shapes

### Challenges

* Create a 2 aggregation for better visualisations

### Steps

1. Download the LV03 Shapes via: http://data.geo.admin.ch/ch.swisstopo-vd.ortschaftenverzeichnis_plz/PLZO_SHP_LV03.zip
  ![grafik](https://user-images.githubusercontent.com/14135678/77164778-dfcc9c80-6aa8-11ea-8acc-f046b7e3b2f0.png)

# Kantone

Download current file at https://www.swisstopo.admin.ch/de/landschaftsmodell-swissboundaries3d#technische_details
Extract the file and import all `*Kanton*` files into mapshaper.org, some good hints can be found here: https://github.com/gitfvb/AptecoGeoShapes/blob/dev-initial/Code-Examples/mapshaper.md
With the following commands you can prepare the files

```
# Showing all fields/properties of the shapefile
- info

# Change projection to WGS84
-proj wgs84

# Create a new field with trimmed canton numbers
-each 'KANTON=KANTONSNUM.toString().trim()'

# Optional: Filter by Kantone
-filter '"15,16,17".indexOf(KANTONSNUM.toString().trim()) > -1'

```

Btw. if you want to use this map with a selector variable that mirrors the current distribution in the cantons, use this expression:

```
FormatNumber(BandUp(
	Rand(999)+1
	;179
;298
;346
;350
;369
;373
;378
;383
;398
;436
;468
;490
;523
;533
;539
;541
;601
;624
;705
;738
;778
;872
;913
;933
;992
)+1
;0)
```

# PLZ

Go to https://data.geo.admin.ch/ and look for something like ´ortschaftenverzeichnis_plz` and then download the `*.shp.zip*` file

Then the same as in Kantone, user mapshaper to transform the files

```
# Showing all fields/properties of the shapefile
- info

# Change projection to WGS84
-proj wgs84

# remove not needed fields
filter-fields ZIP4,STATUS

# simplify maybe over the UI, e.g. simplified to 0.5%

# clean the shape
-clean


```

simplify and export as geojson
and export 


