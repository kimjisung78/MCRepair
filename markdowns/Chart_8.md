# Chart 8 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
source/org/jfree/data/time/Week.java: 173-176
    public Week(Date time, TimeZone zone) {
        // defer argument checking...
-       this(time, RegularTimePeriod.DEFAULT_TIME_ZONE, Locale.getDefault());
+       this(time, zone, Locale.getDefault());
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/data/time/Week.java: 175
this(time, RegularTimePeriod.DEFAULT_TIME_ZONE, Locale.getDefault());
```
<br>

## 3. Correct combined patches per bug type
* T1F: 293
<br><br>

## 4. Examples of correct patches
### 4.1. 293rd patch - T1F
#### I. Fixed Result
```java
source/org/jfree/data/time/Week.java: 175
-   this(time, RegularTimePeriod.DEFAULT_TIME_ZONE, Locale.getDefault());
+   this(time, zone, Locale.getDefault());
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/data/time/Week.java: 175
this(time, zone, Locale.getDefault());
```
<br><br>