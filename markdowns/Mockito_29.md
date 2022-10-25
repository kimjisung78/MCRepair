# Mockito 29 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/org/mockito/internal/matchers/Same.java: 29
-   description.appendText(wanted.toString());
+   description.appendText(wanted == null ? "null" : wanted.toString());
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/org/mockito/internal/matchers/Same.java: 29
description.appendText(wanted.toString());
```
<br>

## 3. Correct combined patches per bug type
* T1F: 346
<br><br>

## 4. Examples of correct patches
### 4.1. 346th patch - T1F
#### I. Fixed Result
```java
src/org/mockito/internal/matchers/Same.java: 29
-   description.appendText(wanted.toString());
+   description.appendText(String.valueOf(wanted));
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/org/mockito/internal/matchers/Same.java: 29
description.appendText(String.valueOf(wanted));
```

#### III. Decided Reason
```String.valueOf(wanted)``` is equivalent to ```wanted == null ? "null" : wanted.toString()``` as follows.
```java
System.out.println(String.valueOf(null)); // "null"
System.out.println(String.valueOf("346")); // "346"
```
<br><br>