# Math 85 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/math/analysis/solvers/UnivariateRealSolverUtils.java: 198
-   if (fa * fb >= 0.0) {
+   if (fa * fb > 0.0) {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/math/analysis/solvers/UnivariateRealSolverUtils.java: 198
if (fa * fb >= 0.0) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 1
<br><br>

## 4. Examples of correct patches
### 4.1. 1st patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/math/analysis/solvers/UnivariateRealSolverUtils.java: 198
-   if (fa * fb >= 0.0) {
+   if (fa * fb > 0.0) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/math/analysis/solvers/UnivariateRealSolverUtils.java: 198
if (fa * fb > 0.0) {
```  
<br><br>