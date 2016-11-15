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

### Craftsmanship advice

> Overuse of `isNotEmpty` / `isNotBlank` may be a sign of code smells such as primitive obsession and anemic domain model.

Note:
- Everything is a String, instead of meaningful classes
- Domain model only has getters and setters, but no constructor that makes sure classes are constructed into valid state
- Example: Customer without Customer ID?

---

### Beyond StringUtils

`ArrayUtils, BooleanUtils, CharSetUtils, CharUtils, ClassPathUtils, ClassUtils, DateFormatUtils, DateUtils, DurationFormatUtils, EnumUtils, ExceptionUtils, IEEE754rUtils, LocaleUtils, NumberUtils, ObjectUtils, RandomStringUtils, RandomUtils, SerializationUtils, StringEscapeUtils, StringUtils, SystemUtils, ThreadUtils, WordUtils`

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
boolean win10 = SystemUtils.IS_OS_WINDOWS_10;
String javaHomePath = SystemUtils.JAVA_HOME;
File javaHome = SystemUtils.getJavaHome();
```

- Which Java Version am I running on?

```java
SystemUtils.isJavaVersionAtLeast(JavaVersion.JAVA_1_7);
```

Note:
- anything below JAVA_1_6 doesn't make sense since Lang3 is Java 6

---

```
import static org.junit.Assume.assumeTrue;
import static org.apache.commons.lang3.JavaVersion.JAVA_1_7

@Test
public void java_version_specific_test() {
  assumeAtLeast(JAVA_1_7);
  
  // do something only possbile with Java 7+
}

private static assumeAtLeast(JavaVersion version) {
  assumeTrue(SystemUtils.isJavaVersionAtLeast(version));
}
```

---

### StrSubstitutor

- provides a convenient way to do string substitutions
- think of it as a template engine in one class

```
String replaced = StrSubstitutor.replaceSystemProperties(
      "You are running with java.version = ${java.version}" +
      " and os.name = ${os.name}.");
```

---

### Custom substitutions

```
Map<String, String> values = ...
StrSubstitutor strSubstitutor = new StrSubstitutor(values);
strSubstitutor.replace(
        "Template with {customKey} and {another:-FallBack}");
```

---

### ...and there is more!

- Mutable variants of primitive wrapper types
- (Im)MutablePair, (Im)MutableTriple
- Equals-, Hashcode-, ToString-, DifferenceBuilder
- ContextedRuntimeException, ContextedException
- Text translations and escaping

---

### Commons Lang and Java 8/9?

- Commons Lang 3.4 requires Java 6
- Commons Lang 3.5 will require Java 7
- Discussions on the ML about Java 8
- Build works on Java 9 but problems with Locales

Note:
- Leverage Java 8 features (default methods, Lambdas)
- Build new APIs on Java 8 APIs (java.util.function, java.time)
- Upgrade now without breaking compatibility vs. Commons Lang 4
