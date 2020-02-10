# xxx
```OverpassTurbo
/* all postcodes in Hungary */
area["name"="Magyarország"][boundary=administrative]->.myarea;
rel(area.myarea)["boundary"="postal_code"];
out geom;
```

## Source

* http://www.geox.hu/vector-map-of-hungary/ - paid




