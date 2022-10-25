# Math 82 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/optimization/linear/SimplexSolver.java: 82
-   if (MathUtils.compareTo(entry, 0, epsilon) >= 0) {
+   if (MathUtils.compareTo(entry, 0, epsilon) > 0) {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/optimization/linear/SimplexSolver.java: 82
if (MathUtils.compareTo(entry, 0, epsilon) >= 0) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 13
<br><br>

## 4. Examples of correct patches
### 4.1. 13rd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/optimization/linear/SimplexSolver.java: 82
-   if (MathUtils.compareTo(entry, 0, epsilon) >= 0) {
+   if (MathUtils.compareTo(entry, 0, epsilon) > 0) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/optimization/linear/SimplexSolver.java: 82
if (MathUtils.compareTo(entry, 0, epsilon) > 0) {
```  
<br><br>