# Postleitzahl

## Sources

* [Apteco Benelux](https://www.apteco.nl/) - paid
* [Spotzi](https://www.spotzi.com/en/maps/boundaries/4-digit-postal-code-belgium/) - paid
* OpenStreetMap via OverpassTurbo - free
* OpenDataSoft: https://public.opendatasoft.com/explore/dataset/openpostcodevlakkenpc4/export/?location=8,51.75084,5.16632&basemap=jawg.streets
* https://www.europeandataportal.eu/data/datasets/6e6ccd59-a4b8-40f3-b52d-3be8060ad759?locale=en Download, unzip and open the gpkg file in QGIS

### Overpass Turbo Query (this only extracts some postcodes and mostly BAG, woonplaatscode)

```javascript
/* all postal codes in nederlands */
area["name:de"="Niederlande"]->.myarea;
rel(area.myarea)[boundary=administrative][admin_level=10];
/*added by auto repair*/
(._;>;);
/*end of auto repair*/
out;
```
