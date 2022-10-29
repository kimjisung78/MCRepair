# Math 63
* <h4>Bug type: Type 2 (T1B / T1F, T2F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 5 locations (1 used location / 1, 5 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 416-418
    public static boolean equals(double x, double y) {
-       return (Double.isNaN(x) && Double.isNaN(y)) || x == y;
+       return equals(x, y, 1);
    }
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 417
return (Double.isNaN(x) && Double.isNaN(y)) || x == y;
```
<br>

## 3. Correct combined patches per bug type
* T1F: 332, 341, 376
* T2F: 423, 430, 442
<br><br>

## 4. Examples of correct patches
### 4.1. 332nd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 121
-   return (Double.isNaN(x) && Double.isNaN(y)) || x == y;
+   return x==y;
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 121
return x==y;
```

#### III. Decided Reason 
The result of a floating-point comparison, as determined by the specification of the IEEE 754 standard, is:
Floating-point equality testing is performed in accordance with the rules of the IEEE 754 standard:
* If either operand is NaN, then the result of == is false but the result of != is true. Indeed, the test x!=x is true if and only if the value of x is NaN. The methods Float.isNaN and Double.isNaN may also be used to test whether a value is NaN.
* Positive zero and negative zero are considered equal. For example, -0.0==0.0 is true.
* Otherwise, two distinct floating-point values are considered unequal by the equality operators. In particular, there is one value representing positive infinity and one value representing negative infinity; each compares equal only to itself, and each compares unequal to all other values.
```java
Float.NEGATIVE_INFINITY == Float.NEGATIVE_INFINITY // true
Double.NEGATIVE_INFINITY == Double.NEGATIVE_INFINITY // true
Float.POSITIVE_INFINITY == Float.POSITIVE_INFINITY // true
Double.NEGATIVE_INFINITY == Double.NEGATIVE_INFINITY // true
-0.0==0.0 // true
Float.NaN == Float.NaN // false
Double.NaN == Double.NaN // false
```
Because ```==``` operator provides mathematical comparisons, it returns false for ```NaN == NaN``` and true for ```-0.0 == 0.0```. Therefore, using ```==``` operator except for ```NaN``` can fix the bug.
<br>

### 4.2. 442nd patch - T2F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 121
-   return (Double.isNaN(x) && Double.isNaN(y)) || x == y;
+   if (x == y) {
+       return true; 
+   } else { 
+       return false; 
+   }
```  

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 5 locations
```java
src/main/java/org/apache/commons/math/util/MathUtils.java: 121
if (x == y) {
    return true;
} else { 
    return false;
}
```

#### III. Decided Reason 
Its reason is the same as the reason in the 332nd patch.
<br><br>