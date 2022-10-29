# Math 98
* <h4>Bug type: Type 3 (T3B / T3F)</h4>
* <h4>The number of chunks: 2 chunks (2 used chunks / 2 fixed chunks)</h4>
* <h4>The number of locations: 2 locations (2 used locations / 2 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/math/linear/BigMatrixImpl.java: 989-991
    final int nRows = this.getRowDimension();            
    final int nCols = this.getColumnDimension();
-   final BigDecimal[] out = new BigDecimal[v.length];
+   final BigDecimal[] out = new BigDecimal[nRows];
```

```java
src/java/org/apache/commons/math/linear/RealMatrixImpl.java: 779
-   final double[] out = new double[v.length];
+   final double[] out = new double[nRows];
```
<br>

## 2. Used chunks and locations - T3B
* The number of used chunks: 2 chunks
* The number of used locations: 2 locations
```java
src/java/org/apache/commons/math/linear/BigMatrixImpl.java: 991
final BigDecimal[] out = new BigDecimal[v.length];
```

```java
src/java/org/apache/commons/math/linear/RealMatrixImpl.java: 779
final double[] out = new double[v.length];
```
<br>

## 3. Correct combined patches per bug type
* T3F: 5,055, 5,096
<br><br>

## 4. Examples of correct patches
### 4.1. 5,055th patch - T3F
#### I. Fixed Result
```java
src/java/org/apache/commons/math/linear/BigMatrixImpl.java: 991
-   final BigDecimal[] out = new BigDecimal[v.length];
+   final BigDecimal[] out = new BigDecimal[this.data.length];
```

```java
src/java/org/apache/commons/math/linear/RealMatrixImpl.java: 779
-   final double[] out = new double[v.length];
+   final double[] out = new double[this.data.length];
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/java/org/apache/commons/math/linear/BigMatrixImpl.java: 991
final BigDecimal[] out = new BigDecimal[this.data.length];
```

```java
src/java/org/apache/commons/math/linear/RealMatrixImpl.java: 779
final double[] out = new double[this.data.length];
```

### III. Decided Reason
Since ```data``` field is a 2D array, the length of the field is equivalent to the number of rows.
<br>

### 4.2. 5,096th patch - T3F
#### I. Fixed Result
```java
src/java/org/apache/commons/math/linear/BigMatrixImpl.java: 991
-   final BigDecimal[] out = new BigDecimal[v.length];
+   final BigDecimal[] out = new BigDecimal[this.data.length];
```

```java
src/java/org/apache/commons/math/linear/RealMatrixImpl.java: 779
-   final double[] out = new double[v.length];
+   final double[] out = new double[getRowDimension()];
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/java/org/apache/commons/math/linear/BigMatrixImpl.java: 991
final BigDecimal[] out = new BigDecimal[this.data.length];
```

```java
src/java/org/apache/commons/math/linear/RealMatrixImpl.java: 779
final double[] out = new double[getRowDimension()];
```

### III. Decided Reason
Its reason is the same as the reason in the 5,055th patch.
<br><br>