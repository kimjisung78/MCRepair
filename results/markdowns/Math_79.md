# Math 79
* <h4>Bug type: Type 3 (T3B / T1F, T3F)</h4>
* <h4>The number of chunks: 2 chunks (2 used chunks / 1, 2 fixed chunks)</h4>
* <h4>The number of locations: 2 locations (2 used locations / 1, 2 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1623-1629
    public static double distance(int[] p1, int[] p2) {
-       int sum = 0;
+       double sum = 0;
        for (int i = 0; i < p1.length; i++) {
-           final int dp = p1[i] - p2[i];
+           final double dp = p1[i] - p2[i];
            sum += dp * dp;
        }
        return Math.sqrt(sum);
```
<br>

## 2. Used chunks and locations - T3B
* The number of used chunks: 2 chunks
* The number of used locations: 2 locations
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1624
int sum = 0;
```

```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1626
final int dp = p1[i] - p2[i];
```
<br>

## 3. Correct combined patches per bug type
* T1F: 153, 160, 258, 295, 296, 488, 422
* T3F: 59, 64, 368, 381, 383
<br><br>

## 4. Examples of correct patches
### 4.1. 59th patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1624-1628
-   int sum = 0;
+   double sum = 0;
    for (int i = 0; i < p1.length; i++) {
-       final int dp = p1[i] - p2[i];
+       final double dp = p1[i] - p2[i];
        sum += dp * dp;
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1624
-   int sum = 0;
+   double sum = 0;
```

```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1626
-   final int dp = p1[i] - p2[i];
+   final double dp = p1[i] - p2[i];
```
<br>

### 4.2. 153rd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1624-1628
    int sum = 0;
    for (int i = 0; i < p1.length; i++) {
-       final int dp = p1[i] - p2[i];
+       final double dp = p1[i] - p2[i];
        sum += dp * dp;
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 1626
-   final int dp = p1[i] - p2[i];
+   final double dp = p1[i] - p2[i];
```

### III. Explanation
```distance``` method just returns the distance between the two points for checking to overlap. Therefore, only changing Location 1626 check to the overlap.
<br><br>