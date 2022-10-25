# Lang 59 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/lang/text/StrBuilder.java: 882-885
    int strLen = str.length();
    if (strLen >= width) {
-       str.getChars(0, strLen, buffer, size);
+       str.getChars(0, width, buffer, size);
    } else {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/text/StrBuilder.java: 884
str.getChars(0, strLen, buffer, size);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 37
<br><br>

## 4. Examples of correct patches
### 4.1. 37th patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/text/StrBuilder.java: 884
-   str.getChars(0, strLen, buffer, size);
+   str.getChars(0, width, buffer, size);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/text/StrBuilder.java: 884
str.getChars(0, width, buffer, size);
```
<br><br>