# Math 72 - Type 3 (T3B / T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 115
-   setResult(yMin, 0);
+   setResult(min, 0);
```

```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 127
-   setResult(yMax, 0);
+   setResult(max, 0);
```
<br>

## 2. Used chunks and locations - 2 chunks / 2 locations
```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 115
setResult(min, 0);
```

```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 127
setResult(max, 0);
```
<br>

## 3. Correct combined patches per bug type
* T3F: 21
<br><br>

## 4. Examples of correct patches
### 4.1. 21st patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 115
-   setResult(yMin, 0);
+   setResult(min, 0);
```

```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 127
-   setResult(yMax, 0);
+   setResult(max, 0);
```

#### II. Fixed chunks and locations - 2 chunk / 2 locations
```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 115
setResult(min, 0);
```

```java
src/main/java/org/apache/commons/math/analysis/solvers/BrentSolver.java: 127
setResult(max, 0);
```
<br><br>