<!-- .slide: data-background="img/background-orange-orig.jpg" data-state="intro" class="center" -->
## Komponenten <!-- .element: class="heading" style="text-align: center;"-->
## Apache Commons IO <!-- .element: class="heading" style="text-align: center;"-->

---

### Einleitung

Hilfsmittel zur Implementierung von I/O Funktionen

- Datei
   - Lesen, Schreiben, Kopieren / Verschieben, Vergleichen
- Verzeichnis
  - (Inhalt) Lesen, Kopieren / Verschieben, Leeren, Löschen
- IO Stream
  - Lesen, Schreiben, Kopieren, Vergleichen
- Weitere Hilfsmittel
  - Dateifilter, IO Streams, Datei Komparatoren

---

### `FileUtils` - Arbeiten mit Dateien

Datei schreiben & lesen

```java
File datei = new File("~/hallo.txt");
FileUtils.writeStringToFile(datei, "Hallo Welt!");
```

```java
String halloWelt = FileUtils.readFileToString(datei);
```

Datei Kopieren

```java
File ziel = new File("~/halloKopie.txt");
FileUtils.copyFile(datei, ziel);
File verzeichnis = new File("~/verzeichnis");
FileUtils.copyFileToDirectory(datei, verzeichnis);
```

Dateiinhalt vergleichen

```java
boolean identisch = FileUtils.contentEquals(datei, ziel);
```

---

### `FileUtils` - Arbeiten mit Verzeichnissen

Kopieren & Verschieben

```java
File quellVerzeichnis = new File("~/Quelle");
File zielVerzeichnis = new File("~/Ziel");
FileUtils.copyDirectory(quellVerzeichnis, zielVerzeichnis);
```

```java
FileUtils.moveDirectory(quellVerzeichnis, zielVerzeichnis);
```

Rekursives Löschen

```java
FileUtils.deleteDirectory(verzeichnis);
```

Verzeichnis leeren (Unterverzeichnisse rekursiv löschen)


```java
FileUtils.cleanDirectory(verzeichnis);
```
