Mit Mapshaper zu arbeiten ist relativ einfach:

* Öffnen von https://mapshaper.org/
* Die Verarbeitung erfolgt immer lokal im Browser, es wird nichts hochgeladen. Mit einem Refresh im Browser kann man frisch starten
* Mit dem Öffnen der Konsole kann man direkt Befehle eingeben.
* Dateien können per Drag&Drop in das Fenster gezogen werden. Ich persönlich benutzte meist geojson- oder shp-Dateien. Bei Shapefiles (shp) muss man darauf achten, dass man mindestens die .shp- und .dbf-Datei reinzieht.
* Übrigens kann die Anwendung auch lokal installiert und über npm installiert und nodejs als CLI genutzt werden.

![grafik](https://user-images.githubusercontent.com/14135678/81678144-b3eae900-9451-11ea-906a-2701568cf673.png)


# Allgemein


`mapshaper -clean` schließt Lücken und entfernte ungültige Geometrien. Ergebnis kann wie hier aussehen:

![grafik](https://user-images.githubusercontent.com/14135678/81679102-4d19ff80-9452-11ea-887f-51287b48bf68.png)


`mapshaper -info` gibt Informationen über die aktuelle Karte wieder:

![grafik](https://user-images.githubusercontent.com/14135678/81679438-83f01580-9452-11ea-979d-ef4e654d2a21.png)

Die Hilfe für die Befehle ist auch sehr praktisch:

![grafik](https://user-images.githubusercontent.com/14135678/81681497-99663f00-9454-11ea-97a9-7d568076f99d.png)

# Geometrien vereinfachen

Dies kann relativ einfach über die Befehle in der CLI oder auch über die GUI erfolgen. Weil es so einfach ist, so geht es über die GUI:

![TinyTake12-05-2020-02-16-12](https://user-images.githubusercontent.com/14135678/81690341-6d01f100-945b-11ea-9760-78ea8df47907.gif)

# Felder hinzufügen und entfernen
`mapshaper -each 'PLZ2=plz.toString().substr(0,2)'` erstellt ein neues Feld, in diesem Beispiel die zweistellige Postleitzahl (auch Postleitregion genannt) auf Basis der ersten beiden Stellen der Postleitzahl:
![grafik](https://user-images.githubusercontent.com/14135678/81680202-214b4980-9453-11ea-9ede-3075fc75d272.png)

---
**Hinweis:** Zur Nutzung von Shapedateien in Apteco werden zwei Felder benötigt:
* FS_CODE
* FS_DESC
Das kann z.B. so realisiert werden:
```
mapshaper -each 'FS_CODE=plz.toString()'
mapshaper -each 'FS_DESC=plz.toString()'
```
---

`mapshaper -drop 'fields=PLZ2'` oder `mapshaper -drop 'fields=FS_CODE,FS_DESC'` entfernt entsprechende Felder aus den Daten.

![grafik](https://user-images.githubusercontent.com/14135678/81681297-789de980-9454-11ea-8ad2-5f51a5bc2206.png)

# Aggregation von Geometrien mit einem Feld

Um die Regionen zusammenzuführen, z.B. PLZ5 zu PLZ2, kann man dies mit dem einfach Befehl `mapshaper -dissolve PLZ2' durchführen:

![TinyTake12-05-2020-01-36-47_v2](https://user-images.githubusercontent.com/14135678/81683821-bb60c100-9456-11ea-80fd-47b16e52c4b9.gif)

Nach dem Vorgang empfiehlt es sich, nochmal ein `mapshaper -clean` auszuführen, um sicher zu sein, dass alle Zusammenfassungen korrekte Geometrien ergeben.

# Projektion anpassen

Bei Geometrien, z.B. aus der Schweiz, aber auch vielen anderen Ländern gibt es meist andere Projektionen als WGS84. Mit mapshaper kann man relativ einfach mittels `mapshaper -proj longlat` oder `mapshaper -proj wgs84`die Projektion ändern.

# Zusammenfassen von mehreren Geometrien

Um z.B. mehrere Länder in einer Karte zusammenzufassen importiert man mehrere Karten. Hier kann man dies sehen und auch dazwischen wechseln:

![grafik](https://user-images.githubusercontent.com/14135678/81684460-45a92500-9457-11ea-80bd-08d4a0c92850.png)

Um diese Karten nun zusammenzufassen, gibt man folgenden Befehl ein:

```
mapshaper -merge-layers target=Netherlands,Germany name=GeNe force
```

![TinyTake12-05-2020-01-55-01](https://user-images.githubusercontent.com/14135678/81685647-6e7dea00-9458-11ea-9ee7-a443bbe12dfb.gif)

Mit einem `mapshaper -clean` kann man sicherstellen, dass nur korrekte Geometrien übrig bleiben.

# Export und Herunterladen

---
**Hinweis:** Für Apteco FastStats wird das Shape-Format benötigt

![grafik](https://user-images.githubusercontent.com/14135678/81680843-0fb67180-9454-11ea-8c73-970d5d0d24f8.png)
---


# Hinweise

Die Screenshots wurden mit der Version `0.5.6` angefertigt:

![grafik](https://user-images.githubusercontent.com/14135678/81682621-37f2a000-9455-11ea-9b8e-f962bca68df8.png)

