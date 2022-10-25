# Math 2 - Type 1 (T1B / T1F)

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

## 2. Used chunks and locations - 1 chunk / 1 location
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

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
return (double) sampleSize * getNumberOfSuccesses() / (double) getPopulationSize();
```

#### III. Decided Reason
To fix bug, the bugs must be change that it converts ```getSampleSize()``` to double.
<br><br>

### 4.2. 219th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
-   return (double) (getSampleSize() * getNumberOfSuccesses()) / (double) getPopulationSize();
+   return (double) sampleSize * getNumberOfSuccesses() / getPopulationSize();
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
return (double) sampleSize * getNumberOfSuccesses() / getPopulationSize();
```

#### III. Decided Reason
Its reason is the same as the reason in the 138th patch.
<br><br>

### 4.3. 394th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
-   return (double) (getSampleSize() * getNumberOfSuccesses()) / (double) getPopulationSize();
+   return (double) getSampleSize() * getNumberOfSuccesses() / (double) getPopulationSize();
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/distribution/HypergeometricDistribution.java: 268
return (double) getSampleSize() * getNumberOfSuccesses() / (double) getPopulationSize()
```

#### III. Decided Reason
Its reason is the same as the reason in the 138th patch.
<br><br>