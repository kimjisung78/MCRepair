# Time 19 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/joda/time/DateTimeZone.java: 900
-   } else if (offsetLocal > 0) {
+   } else if (offsetLocal >= 0) {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/joda/time/DateTimeZone.java: 900
} else if (offsetLocal > 0) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 48, 89
<br><br>

## 4. Examples of correct patches
### 4.1. 48th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/joda/time/DateTimeZone.java: 900
-   } else if (offsetLocal > 0) {
+   } else if (offsetLocal > 0 - 1) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/joda/time/DateTimeZone.java: 900
} else if (offsetLocal > 0 - 1) {
```
<br>

### 4.2. 89th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/joda/time/DateTimeZone.java: 900
-   } else if (offsetLocal > 0) {
+   } else if (offsetLocal >= 0) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/joda/time/DateTimeZone.java: 900
} else if (offsetLocal >= 0) {
```
<br><br>