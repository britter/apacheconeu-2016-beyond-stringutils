<!-- .slide: data-background="img/background-dark-orig.jpg" data-state="intro" class="center" -->
## Komponenten <!-- .element: class="heading" style="text-align: center;"-->
### Apache Commons Validator <!-- .element: class="heading" style="text-align: center;"-->

---

### Überblick

- Nutzereingaben müssen validiert werden
- Häufiges Problem: Datenübertragung als String
- Validierungsroutinen für standardisierte Formate sind bekannt:
  - E-Mail Adressen
  - Datumsangabe
  - Kreditkartennummer
  - ISBN
  - URL

---

### Datum und Zeit

- Prüfung ob ein String ein gültiges Datum darstellt
- Datums-, Zeitvergleich, Zeitzonenanpassung

```java
DateValidator dateValidator = DateValidator.getInstance();
boolean korrekt = dateValidator.isValid("31.05.2007",
    Locale.GERMANY);
// "31.04.2007" >> false
```

- Anpassen der Validierung und Formattierung durch "Pattern"

```java
dateValidator.isValid("05.2007", "MM.yyyy", Locale.GERMANY);
// "13.2007" >> false
```

---

### Zahlen

- Prüfung von Wertebereich, Minimum, Maximum
- Für alle Standardtypen: `Float, Double, Integer, Long, Short, BigDecimal, BigInteger, Byte`

```java
DoubleValidator doubleValidator = DoubleValidator.getInstance();
Double zahl = doubleValidator.validate("9,99",
    Locale.GERMANY);
if (zahl != null) {
  boolean korrekt = doubleValidator.isInRange(zahl, 0, 10);
  // "10,01" >> false
}
```

---

### Prüfsummen

- Kreditkarte, EAN, ISBN, IMEI, ...
- Prüfverfahren: Luhn, EAN13, UPC, ISBN-10, ISBN-13

```java
ISBNValidator isbnValidator = new ISBNValidator();
boolean korrekt = isbnValidator.isValid("389864457X");
// "388864457X" >> false
```

---

### Spezialformate

Email, URL, Domain Name, IP-Adresse, Regular Expression

```java
EmailValidator emailValidator = EmailValidator.getInstance();
boolean korrekt = emailValidator.isValid("max@mustermann.de");
// "max@mustermannde" >> false
```
