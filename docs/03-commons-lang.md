<!-- .slide: data-background="img/background-lightgreen-orig.jpg" data-state="intro" class="center" -->
##  Komponenten <!-- .element: class="heading" -->
### Apache Commons Lang <!-- .element: class="heading" -->

---

### Fokus

Erweiterung der Java Bibliothek um Methoden zur Manipulation der Basis-Klassen: `java.lang`
- Manipulation von String, Boolean, Array, ...
  - Der Klassiker: `StringUtils`
- Einfache Numerik
- Zugriff auf System-Eigenschaften
- Bearbeitung von Datum + Zeit (Stoppuhr)
- Hilfsmittel zur Implementierung von
`hashCode()`, `toString()` und `equals(Object)`

---

### ...Utils

- Methoden für den täglichen Gebrauch
- Statische Methoden für simpelste Verwendung
- Null-Safe
- Thread-Safe

<small>
`ArrayUtils, BooleanUtils, CharSetUtils, CharUtils, ClassUtils, DateFormatUtils, DateUtils, DurationFormatUtils, EnumUtils, ExceptionUtils, LocaleUtils, NumberUtils, ObjectUtils, RandomStringUtils, RandomUtils, SerializationUtils, StringEscapeUtils, StringUtils, SystemUtils, WordUtils`
</small>

---

### `StringUtils` (1/2)

Ist ein String leer (null oder "")?

```java
if (string == null || string == "") { ... }
```

```java
if (StringUtils.isEmpty(string)) { ... }
```

Ist ein String leer oder Leerstring (null, "" oder " ")?


```java
if (string == null || string.length() < 1) { ... }
```

```java
if (StringUtils.isBlank(string)) { ... }
```

---

### `StringUtils` (2/2)

Sind zwei Strings gleich?

```java
if (a != null && a.equals(b)) {
  // gleich
} else if (a == null && b == null) {
  // gleich
}
```

```java
if (StringUtils.equals(a, b)) { ... }
```

---

### `BooleanUtils`

- Konvertierung eines String in einen boolean bzw. Boolean
- Unterscheidung zwischen wahr, falsch und nicht ermittelbar

```java
// Boolean.TRUE
Boolean wahr = BooleanUtils.toBooleanObject("true");
// Boolean.FALSE
Boolean falsch = BooleanUtils.toBooleanObject("off");
// null
Boolean nichtErmittelbar = BooleanUtils.toBooleanObject("Hallo");
```

- Übergabe eines Fallback Wertes

```java
BooleanUtils.toBooleanDefaultIfNull(nichtErmittelbar, true);
```

---

### `DateUtils`

- Addition / Subtraktion von Jahren, Monaten, Wochen, Tagen, Stunden, Minuten, Sekunden, Millisekunden

```java
Date inEinemJahr = DateUtils.addYears(heute, 1);
```

- Datumsvergleich: Derselbe Tag ?

```java
boolean wahr = DateUtils.isSameDay(heuteMorgen, heuteAbend);
```

- Trotzdem wenn möglich lieber Java 8 Time API oder Joda Time verwenden!
