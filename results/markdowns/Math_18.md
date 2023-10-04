# Math 18
* <h4>Bug type: Type 3 (T3B / T3F) => PL (Plausible)</h4>
* <h4>The number of chunks: 4 chunks (4 used chunks / 2 fixed chunks) => 0 chunk (4 used chunks / 0 fixed chunk)</h4>
* <h4>The number of locations: 4 locations (4 used locations / 2 fixed locations) => 0 location (4 used locations / 0 fixed location)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 929-934
    double[] res = new double[x.length];
    for (int i = 0; i < x.length; i++) {
    double diff = boundaries[1][i] - boundaries[0][i];
-       res[i] = (x[i] - boundaries[0][i]) / diff;
+       res[i] = x[i] / diff;
    }            
    return res;
```

```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 955-960
    double[] res = new double[x.length];
    for (int i = 0; i < x.length; i++) {
    double diff = boundaries[1][i] - boundaries[0][i];
-       res[i] = diff * x[i] + boundaries[0][i];
+       res[i] = diff * x[i];
    }            
    return res;
```

```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 990-998
+   final double[] bLoEnc = encode(boundaries[0]);
+   final double[] bHiEnc = encode(boundaries[1]);

    for (int i = 0; i < x.length; i++) {
-       if (x[i] < 0) {
+       if (x[i] < bLoEnc[i]) {
            return false;
        }
-       if (x[i] > 1.0) {
+       if (x[i] > bHiEnc[i]) {
            return false;
        }
    }
```
<br>

## 2. Used chunks and locations
* The number of used chunks: 4 chunks
* The number of used locations: 4 locations
```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 932
res[i] = (x[i] - boundaries[0][i]) / diff;
```

```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 958
res[i] = diff * x[i] + boundaries[0][i];
```

```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 992
if (x[i] < 0) {
```

```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 995
if (x[i] > 1.0) {
```
<br><br>

## 3. Correct combined patches per bug type (Previous)
* T3F: 8,824
<br><br>

## 4. Examples of correct patches (Previous)
### 4.1. 8,824th patch
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 932
-   res[i] = (x[i] - boundaries[0][i]) / diff;
+   res[i] = (x[i]) / diff;
```

```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 958
-   res[i] = diff * x[i] + boundaries[0][i];
+   res[i] = diff * x[i];
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 932
res[i] = (x[i]) / diff;
```

```java
src/main/java/org/apache/commons/math3/optimization/direct/CMAESOptimizer.java: 958
res[i] = diff * x[i];
```

#### III. Explanation
```CMAESOptimizer.java```, which is the source code of the bug, specifies ```Normalizes fitness values to the range [0,1].``` comment. However, locations 992 and 995 in the developer's patch of the bug did not use the range [0,1] for fixing. Therefore, after evaluating the patch correctness again, we removed the 8,824th patch and decided that the bug was plausibly repaired.
<br><br>