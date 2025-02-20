# ToDo

* [ ] put in here partner maps?

# Postleitzahl

https://www.suche-postleitzahl.org/plz-karte-erstellen

# Zensus

# Grid

# Bundesländer

Verwaltungsgebiete 1:2 500 000, Stand 01.01. (VG2500)
![grafik](https://user-images.githubusercontent.com/14135678/77163742-a1ce7900-6aa6-11ea-8b98-91bb50613dfe.png)
Quelle: Bundesamt für Kartographie und Geodäsie
Karten: https://gdz.bkg.bund.de/index.php/default/open-data/verwaltungsgebiete-1-2-500-000-stand-01-01-vg2500.html
Direkter Link: https://daten.gdz.bkg.bund.de/produkte/vg/vg2500/aktuell/vg2500_01-01.utm32s.shape.zip


## Some steps to handle AGS (Gemeinde) in Mapshaper

```Mapshaper
clean
proj wgs84
dissolve AGS
each 'Bundesland=AGS.toString().trim().substring(0, 2)'
clean
# Simplify to 12% retaining all shapes
# Filter to Bayern
filter 'Bundesland == "09"'
```

Reference for all Bundesländer

01 Schleswig-Holstein
02 Hamburg
03 Niedersachsen
04 Bremen
05 Nordrhein-Westfalen
06 Hessen
07 Rheinland-Pfalz
08 Baden-Württemberg
09 Bayern
10 Saarland
11 Berlin
12 Brandenburg
13 Mecklenburg-Vorpommern
14 Sachsen
15 Sachsen-Anhalt
16 Thüringen
