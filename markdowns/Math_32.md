# Math 32 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/geometry/euclidean/twod/PolygonsSet.java: 135-136
    final BSPTree<Euclidean2D> tree = getTree(false);
-   if ((Boolean) tree.getAttribute()) {
+   if (tree.getCut() == null && (Boolean) tree.getAttribute()) {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/geometry/euclidean/twod/PolygonsSet.java: 136
if ((Boolean) tree.getAttribute()) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 194
<br><br>

## 4. Examples of correct patches
### 4.1. 194th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/geometry/euclidean/twod/PolygonsSet.java: 136
-   if ((Boolean) tree.getAttribute()) {
+   if (tree.getAttribute() instanceof Boolean) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/geometry/euclidean/twod/PolygonsSet.java: 136
if (tree.getAttribute() instanceof Boolean) {
```

#### III. Decided Reason
To fix the bug, the bug must be changed that it checks that ```tree.getAttribute()``` can convert to ```Boolean``` class.
<br><br>