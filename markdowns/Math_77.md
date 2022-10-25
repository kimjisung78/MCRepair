# Math 77 - Type 3 (T3B / T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 721
-   max += Math.max(max, Math.abs(a));
+   max = Math.max(max, Math.abs(a));
```

```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 498-506
-   public double getLInfNorm() {
-       double max = 0;
-       Iterator iter = entries.iterator();
-       while (iter.hasNext()) {
-           iter.advance();
-           max += iter.value();
-       }
-       return max;
-   }
```
<br>

## 2. Used chunks and locations - 2 chunks / 10 locations
```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 721
max += Math.max(max, Math.abs(a));
```

```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 498-506
public double getLInfNorm() {
    double max = 0;
    Iterator iter = entries.iterator();
    while (iter.hasNext()) {
        iter.advance();
        max += iter.value();
    }
    return max;
}
```
<br>

## 3. Correct combined patches per bug type
* T3F: 2,903, 2,912
<br><br>

## 4. Examples of correct patches
### 4.1. 2,903rd patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 721
-   max += Math.max(max, Math.abs(a));
+   max = Math.max(max, Math.abs(a));
```

```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 498
-   public double getLInfNorm() {
+   public double getLInfNormal() {
```

#### II. Fixed chunks and locations - 2 chunks / 2 locations
```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 721
max = Math.max(max, Math.abs(a));
```

```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 498
public double getLInfNormal() {
```

### III. Decided Reason
Since ```getLInfNorm``` method is not called in ```ArrayRealVector.java```, the method is equivalent to the deletion.
<br>

### 4.2. 2,912nd patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 721
-   max += Math.max(max, Math.abs(a));
+   max = Math.max(max, Math.abs(a));
```

```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 498
-   public double getLInfNorm() {
+   public double getLinfNorm() {
```

#### II. Fixed chunks and locations - 2 chunks / 2 locations
```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 721
max = Math.max(max, Math.abs(a));
```

```java
src/main/java/org/apache/commons/math/linear/ArrayRealVector.java: 498
public double getLinfNorm() {
```

### III. Decided Reason
Its reason is the same as the reason in the 2,903rd patch.
<br><br>