<!-- .slide: data-background="img/background-orange-orig.jpg" data-state="intro" class="center" -->
## Components <!-- .element: class="heading" style="text-align: center;"-->
### Apache Commons CSV <!-- .element: class="heading" style="text-align: center;"-->

---

### Introduction

- Character Separated Value (CSV) is still a common data exchange format

> "We don't need a library for this! That's just a spilt at the commas!"

- Problem: Although CSV is standardized (RTF-4180) there are a lot of variants

Note:
- Question: Who has written his own CSV parser already?

---

### CSV Variants

CSV format variants differ in:

- delimiter
- line break character
- quoting
- escaping
- headers or not

The "simple split" becomes a nightmare

Note:
- Although XML is quite a complex standard, it is well defined

---

### Parsing with `CSVFormat`

Predefined Formats:

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

### Customizing `CSVFormat`

- Existing formats can be customized
- ...or created from scratch using `newFormat(char)`

```java
CSVFormat myFormat = CSVFormat.RTF4180
    .withSeparator(';')
    .withHeader("CustomerNr", "Name", "First Name", "Birthday")
    .withIgnoreEmptyLines(true);
```

Note:
- Use Enum as header
- It will pick enum value names as headers in enum order

---

### Conclusion

- Seemingly simple tasks can become complex
- Don't reinvent the Wheel - Remember Ritter's law!
- Apache Commons CSV is:
  - easy
  - customizable
  - fast

---

### Limitations

- Printing does not support all features (e.g. crazy line break characters)
- No support for mapping data directly into Java objects
