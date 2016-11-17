<!-- .slide: data-background="img/background-green-16x9.png" data-state="intro" class="center" -->
## Misc <!-- .element: class="heading" style="text-align: center;"-->

---

### Apache Commons Validator

- Credit card numbers, EAN, ISBN, IMEI, ...
- Check digits: Luhn, EAN13, UPC, ISBN-10, ISBN-13

```java
CreditCardValidator ccv = new CreditCardValidator(CreditCardValidator.VISA);
boolean korrekt = ccv.isValid("3435 4356 45342");
```

---

### Apache Commons IO

- File related operations
- tree walking with filter

```
List<String> lines = IOUtils.readLines(inputStream);
```

---

### Apache Commons Compress

- All commons archive formats
- Beware: In the end this is Java!

```

```

---

### Apache Commons VFS

- Access different file systems

```

```

