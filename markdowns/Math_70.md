# Math 70 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/analysis/solvers/BisectionSolver.java: 72
-   return solve(min, max);
+   return solve(f, min, max);
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/analysis/solvers/BisectionSolver.java: 72
return solve(f, min, max);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 28
<br><br>

## 4. Examples of correct patches
### 4.1. 28th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/analysis/solvers/BisectionSolver.java: 72
-   return solve(min, max);
+   return solve(f, min, max);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/analysis/solvers/BisectionSolver.java: 72
return solve(f, min, max);
```  
<br><br>