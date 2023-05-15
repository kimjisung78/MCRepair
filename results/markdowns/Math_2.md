# Math 2
* <h4>Bug type: Type 1 (T1B / T1F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 1 location (1 used location / 1 fixed location)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 265-259
    * size {@code n}, the mean is {@code n * m / N}.
    */
    public double getNumericalMean() {
-       return (double) (getSampleSize() * getNumberOfSuccesses()) / (double) getPopulationSize();
+       return getSampleSize() * (getNumberOfSuccesses() / (double) getPopulationSize());
    }
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
return (double) (getSampleSize() * getNumberOfSuccesses()) / (double) getPopulationSize();
```
<br>

## 3. Correct combined patches per bug type
* T1F: 138, 217, 219, 298, 394, 420
<br><br>

## 4. Examples of correct patches
### 4.1. 138th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
-   return (double) (getSampleSize() * getNumberOfSuccesses()) / (double) getPopulationSize();
+   return (double) sampleSize * getNumberOfSuccesses() / (double) getPopulationSize();
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
return (double) sampleSize * getNumberOfSuccesses() / (double) getPopulationSize();
```

#### III. Explanation
To fix the bug, its source code must be changed that it converts ```sampleSize``` field to double.
<br><br>

### 4.2. 219th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
-   return (double) (getSampleSize() * getNumberOfSuccesses()) / (double) getPopulationSize();
+   return (double) sampleSize * getNumberOfSuccesses() / getPopulationSize();
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
return (double) sampleSize * getNumberOfSuccesses() / getPopulationSize();
```

#### III. Explanation
Its reason is the same as the reason in the 138th patch.
<br><br>

### 4.3. 394th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
-   return (double) (getSampleSize() * getNumberOfSuccesses()) / (double) getPopulationSize();
+   return (double) getSampleSize() * getNumberOfSuccesses() / (double) getPopulationSize();
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
return (double) getSampleSize() * getNumberOfSuccesses() / (double) getPopulationSize()
```

#### III. Explanation
Its reason is the same as the reason in the 138th patch.
<br><br>