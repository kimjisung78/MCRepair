# Math 27 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/fraction/Fraction.java: 596-598
    public double percentageValue() {
-       return multiply(100).doubleValue();
+       return 100 * doubleValue();
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/fraction/Fraction.java: 597
return multiply(100).doubleValue();
```
<br>

## 3. Correct combined patches per bug type
* T1F: 389
<br><br>

## 4. Examples of correct patches
### 4.1. 389th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/fraction/Fraction.java: 597
-   return multiply(100).doubleValue();
+   return doubleValue() * 100.0;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/fraction/Fraction.java: 597
return doubleValue() * 100.0;
```
<br><br>