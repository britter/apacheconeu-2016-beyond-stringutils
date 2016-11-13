<!-- .slide: data-background="img/background-lightgreen-orig.jpg" data-state="intro" class="center" -->
##  Components <!-- .element: class="heading" -->
### Apache Commons Lang <!-- .element: class="heading" -->

---

### First example

```java
if (string == null || string == "") { ... }
```

```java
if (StringUtils.isEmpty(string)) { ... }
```

Note:
- yeah, code!
- boring, everybody knows this
- More methods like this for isBlank, anyBlank, etc.
- generally all methods are null-safe if not documented otherwise

---

### Beyond StringUtils

`ArrayUtils, BooleanUtils, CharSetUtils, CharUtils, ClassUtils, DateFormatUtils, DateUtils, DurationFormatUtils, EnumUtils, ExceptionUtils, LocaleUtils, NumberUtils, ObjectUtils, RandomStringUtils, RandomUtils, SerializationUtils, StringEscapeUtils, StringUtils, SystemUtils, WordUtils`

---

### `BooleanUtils`

```java
// Boolean.TRUE
Boolean isTrue = BooleanUtils.toBooleanObject("true");
// Boolean.FALSE
Boolean isFalse = BooleanUtils.toBooleanObject("off");
// null
Boolean isNull = BooleanUtils.toBooleanObject("Hello");
```

- With fallback...

```java
BooleanUtils.toBooleanDefaultIfNull(isNull, true);
```

Note:
- only really usuable for englisch applications

---

### `DateUtils`

- Calculations on date objects

```java
Date nextYear = DateUtils.addYears(heute, 1);
```

- Date comparision: Same day?

```java
boolean isTrue = DateUtils.isSameDay(thisMorning, thisEvening);
```

- If possible use Java 8 Time API!

Note:
- Most regressions
- Problem with Java 9

---

### `SystemUtils`

- Easy access to Java system properties

```java
SystemUtils.IS_OS_WINDOWS_10; // hopefully this is false...
SystemUtils.JAVA_HOME;
SystemUtils.getJavaHome();
```

- Which Java Version am I running on?

```java
SystemUtils.isJavaVersionAtLeast(JavaVersion.JAVA_1_7);
```
