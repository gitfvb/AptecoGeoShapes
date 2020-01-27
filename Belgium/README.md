# Postleitzahl

## Sources

* [Apteco Benelux](https://www.apteco.nl/) - paid
* [Spotzi](https://www.spotzi.com/en/maps/boundaries/4-digit-postal-code-belgium/) - paid
* OpenStreetMap via OverpassTurbo - free

### Overpass Turbo Query


```javascript
/* all postcodes in belgium */
area["name"="België / Belgique / Belgien"][boundary=administrative]->.myarea;
rel(area.myarea)["boundary"="postal_code"];
out geom;
```