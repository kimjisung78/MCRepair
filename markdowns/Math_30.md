# Math 30 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
-   final int n1n2prod = n1 * n2;
+   final double n1n2prod = n1 * n2;
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
final int n1n2prod = n1 * n2;
```
<br>

## 3. Correct combined patches per bug type
* T1F: 41, 46, 74, 359, 360
<br><br>

## 4. Examples of correct patches
### 4.1. 41st patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
-   final int n1n2prod = n1 * n2;
+   final long n1n2prod = n1 * n2;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
final long n1n2prod = n1 * n2;
```
<br>

### 4.2. 46th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
-   final int n1n2prod = n1 * n2;
+   final double n1n2prod = n1 * n2;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
final double n1n2prod = n1 * n2;
```
<br>

### 4.3. 360th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
-   final int n1n2prod = n1 * n2;
+   double n1n2prod = n1 * n2;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/stat/inference/MannWhitneyUTest.java: 173
double n1n2prod = n1 * n2;
```
<br><br>