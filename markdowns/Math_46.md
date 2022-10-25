# Math 46 - Type 3 (T3B / T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/complex/Complex.java: 258-261
    if (divisor.isZero) {
        // return isZero ? NaN : INF; // See MATH-657
-       return isZero ? NaN : INF;
+       return NaN;
    }
```

```java
src/main/java/org/apache/commons/math/complex/Complex.java: 295-298
    if (divisor == 0d) {
        // return isZero ? NaN : INF; // See MATH-657
-       return isZero ? NaN : INF;
+       return NaN;
    }
```                  
<br>

## 2. Used chunks and locations - 2 chunks / 2 locations
```java
src/main/java/org/apache/commons/math/complex/Complex.java: 260
return isZero ? NaN : INF;
```

```java
src/main/java/org/apache/commons/math/complex/Complex.java: 297
return isZero ? NaN : INF;
```
<br>

## 3. Correct combined patches per bug type
* T3F: 1,979
<br><br>

## 4. Examples of correct patches
### 4.1. 1,979th patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/complex/Complex.java: 260
-   return isZero ? NaN : INF;
+   return isZero ? NaN : NaN;
```

```java
src/main/java/org/apache/commons/math/complex/Complex.java: 297
-   return isZero ? NaN : INF;
+   return NaN;
```

#### II. Fixed chunks and locations - 2 chunks / 2 locations
```java
src/main/java/org/apache/commons/math/complex/Complex.java: 260
return isZero ? NaN : NaN;
```

```java
src/main/java/org/apache/commons/math/complex/Complex.java: 297
return NaN;
```
<br><br>