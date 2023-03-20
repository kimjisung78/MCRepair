# Math 22
* <h4>Bug type: Type 3 (T3B / T3F)</h4>
* <h4>The number of chunks: 2 chunks (2 used chunks / 2 fixed chunks)</h4>
* <h4>The number of locations: 2 locations (2 used locations / 2 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/distribution/FDistribution.java: 274-276
    public boolean isSupportLowerBoundInclusive() {
-       return true;
+       return false;
    }
```

```java
src/main/java/org/apache/commons/math3/distribution/UniformRealDistribution.java: 183-185
    public boolean isSupportUpperBoundInclusive() {
-       return false;
+       return true;
    }
```
<br>

## 2. Used chunks and locations - T3B
* The number of used chunks: 2 chunks
* The number of used locations: 2 locations
```java
src/main/java/org/apache/commons/math3/distribution/FDistribution.java: 275
return true;
```

```java
src/main/java/org/apache/commons/math3/distribution/UniformRealDistribution.java: 184
return false;
```
<br>

## 3. Correct combined patches per bug type
* T3F: 8,703
<br><br>

## 4. Examples of correct patches
### 4.1. 8,703th patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/distribution/FDistribution.java: 275
-   return true;
+   return null != null;
```

```java
src/main/java/org/apache/commons/math3/distribution/UniformRealDistribution.java: 184
-   return false;
+   return true;
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/main/java/org/apache/commons/math3/complex/Complex.java: 305
return INF;
```

#### III. Explanation
```null != null``` is always false.
<br><br>