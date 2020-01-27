# Postleitzahl

## Sources

* [Apteco Benelux](https://www.apteco.nl/) - paid
* [Spotzi](https://www.spotzi.com/en/maps/boundaries/4-digit-postal-code-belgium/) - paid
* OpenStreetMap via OverpassTurbo - free

### Overpass Turbo Query

```javascript
/* all postal codes in nederlands */
area["name:de"="Niederlande"]->.myarea;
rel(area.myarea)[boundary=administrative][admin_level=10];
/*added by auto repair*/
(._;>;);
/*end of auto repair*/
out;
```