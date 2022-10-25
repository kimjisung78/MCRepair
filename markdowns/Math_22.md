# Math 22 - Type 3 (T3B / T3F)

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

## 2. Used chunks and locations - 2 chunks / 2 locations
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

#### II. Fixed chunks and locations - 2 chunks / 2 locations
```java
src/main/java/org/apache/commons/math3/complex/Complex.java: 305
return INF;
```

#### III. Decided Reason
```null != null``` is false.
<br><br>