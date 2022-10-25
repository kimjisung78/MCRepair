# Math 5 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/complex/Complex.java: 304-306
    if (real == 0.0 && imaginary == 0.0) {
-       return NaN;
+       return INF;
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/complex/Complex.java: 305
return NaN;
```
<br>

## 3. Correct combined patches per bug type
* T1F: 218
<br><br>

## 4. Examples of correct patches
### 4.1. 218th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/complex/Complex.java: 305
-   return NaN;
+   return INF;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/complex/Complex.java: 305
return INF;
```
<br><br>