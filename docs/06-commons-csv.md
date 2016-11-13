<!-- .slide: data-background="img/background-dark-orig.jpg" data-state="intro" class="center" -->
## Komponenten <!-- .element: class="heading" style="text-align: center;"-->
### Apache Commons CSV <!-- .element: class="heading" style="text-align: center;"-->

---

### Einleitung

- Character Separated Value (CSV) heute immer noch gebräuchliches Format

> "Dafür brauchen wir keine Library. Das ist doch nur ein split am Komma!"

- Problem: CSV ist zwar standardisiert (RTF-4180) aber es gibt viele Varianten

---

### CSV Varianten

CSV Formate unterscheiden sich in:

- Trennzeichen
- Zeilenumbruch Zeichen
- Quoting
- Escaping
- Mit oder Ohne Header

Aus dem "einfachen split" wird ein Alptraum

---

### Parsen mit `CSVFormat`

Vordefinierte Formate:

`EXCEL, MYSQL, TDF, RTF-4180`

```java
Reader in = new FileReader("path/to/file.csv");
Iterable<CSVRecord> records = CSVFormat.EXCEL.parse(in);
for (CSVRecord record : records) {
    String lastName = record.get("Last Name");
    String firstName = record.get("First Name");
}
```

---

### `CSVFormat` Anpassen

- Vorhandene Formate lassen sich anpassen
- Erzeugung komplett neuer Formate mit `newFormat(char)`

```java
CSVFormat myFormat = CSVFormat.RTF4180
    .withSeparator(';')
    .withHeader("KundenNr", "Name", "Vorname", "Geburtsdatum")
    .withIgnoreEmptyLines(true);
```

---

### Fazit

- Vermeintliche einfache Aufgaben werden schnell komplex
- Don't reinvent the Wheel
- Apache Commons CSV ist:
  - einfach
  - anpassbar
  - schnell
