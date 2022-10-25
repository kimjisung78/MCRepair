# Lang 6 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/lang3/text/translate/CharSequenceTranslator.java: 94-96
    for (int pt = 0; pt < consumed; pt++) {
-       pos += Character.charCount(Character.codePointAt(input, pos));
+       pos += Character.charCount(Character.codePointAt(input, pt));
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/lang3/text/translate/CharSequenceTranslator.java: 95
pos += Character.charCount(Character.codePointAt(input, pos));
```
<br>

## 3. Correct combined patches per bug type
* T1F: 55
<br><br>

## 4. Examples of correct patches
### 4.1. 55th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/text/translate/CharSequenceTranslator.java: 95
-   pos += Character.charCount(Character.codePointAt(input, pos));
+   pos += Character.charCount(Character.codePointAt(input, pt));
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/lang3/text/translate/CharSequenceTranslator.java: 95
pos += Character.charCount(Character.codePointAt(input, pt));
```
<br><br>