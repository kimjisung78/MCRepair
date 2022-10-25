# Lang 57 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/lang/LocaleUtils.java: 222-224
    public static boolean isAvailableLocale(Locale locale) {
-       return cAvailableLocaleSet.contains(locale);
+       return availableLocaleList().contains(locale);
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/LocaleUtils.java: 223
return cAvailableLocaleSet.contains(locale);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 342
<br><br>

## 4. Examples of correct patches
### 4.1. 342nd patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/LocaleUtils.java: 223
-   return cAvailableLocaleSet.contains(locale);
+   return availableLocaleList().contains(locale);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/LocaleUtils.java: 223
return availableLocaleList().contains(locale);
```
<br><br>