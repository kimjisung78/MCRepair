# Time 4 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/joda/time/Partial.java: 464-465
-   Partial newPartial = new Partial(iChronology, newTypes, newValues);
+   Partial newPartial = new Partial(newTypes, newValues, iChronology);
    iChronology.validate(newPartial, newValues);
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/joda/time/Partial.java: 464
Partial newPartial = new Partial(iChronology, newTypes, newValues);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 20
<br><br>

## 4. Examples of correct patches
### 4.1. 20th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/joda/time/Partial.java: 464
-   Partial newPartial = new Partial(iChronology, newTypes, newValues);
+   Partial newPartial = new Partial(newTypes, newValues);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/joda/time/Partial.java: 464
Partial newPartial = new Partial(newTypes, newValues);
```

#### III. Decided Reason
The validation result of ```Partial newPartial = new Partial(newTypes, newValues);``` is equivalent to the validation result of ```Partial newPartial = new Partial(newTypes, newValues, iChronology);```.
<br><br>