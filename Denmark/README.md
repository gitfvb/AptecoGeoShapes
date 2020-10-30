
# Steps to download

1. Register at: https://download.kortforsyningen.dk/ and click: `Opret ny bruger` (create a user)
2. Follow the registration
3. To download the map, use the ftp portal or direct link: ftp://ftp.kortforsyningen.dk/landinddelinger/dagi/SHAPE/DAGIREF_SHAPE_UTM32-EUREF89.zip

# Steps to make the maps better

## Extract Denmark

* Download "Countries, 2016 - Administrative Units - Dataset" from Eurostat
* Import into QGIS the file `CNTR_RG_01M_2016_4326.geojson`
* Select Denmark and Export selected objects as file like `denmark.json`
* Open `denmark.json` in mapshaper

Maybe this can also be done in mapshaper directly, I am open for feedback

## Clean Denmark map

* Drag on the files POSTNUMMER.dbf, POSTNUMMER.prj, POSTNUMMER.shp and POSTNUMMER.shx into mapshaper
* Using commands
```
mapshaper -clean
mapshaper -proj wgs84
mapshaper -clip denmark
mapshaper -each FS_CODE="DK--"+POSTNR_TXT
mapshaper -each FS_DESC=POSTBYNAVN
```
* Optionally simplify the map
* Download as geojson or shp files



# Other notes

Not checked in detail, maybe at http://dawa.aws.dk/