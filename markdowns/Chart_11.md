# Chart 11 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
source/org/jfree/chart/util/ShapeUtilities.java: 274-277
    PathIterator iterator1 = p1.getPathIterator(null);
-   PathIterator iterator2 = p1.getPathIterator(null);
+   PathIterator iterator2 = p2.getPathIterator(null);
    double[] d1 = new double[6];
    double[] d2 = new double[6];
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/util/ShapeUtilities.java: 275
PathIterator iterator2 = p1.getPathIterator(null);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 146, 170, 410
<br><br>

## 4. Examples of correct patches
### 4.1. 146th patch - T1F
#### I. Fixed Result
```java
source/org/jfree/chart/util/ShapeUtilities.java: 275
-   PathIterator iterator2 = p1.getPathIterator(null);            
+   PathIterator iterator2 = p2.getPathIterator(null); 
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/util/ShapeUtilities.java: 275
PathIterator iterator2 = p2.getPathIterator(null);
```
<br>

### 4.2. 170th patch - T1F
#### I. Evaluated Result
```java
source/org/jfree/chart/util/ShapeUtilities.java: 274
-   PathIterator iterator1 = p1.getPathIterator(null);            
+   PathIterator iterator1 = p2.getPathIterator(null); 
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/util/ShapeUtilities.java: 274
PathIterator iterator1 = p2.getPathIterator(null);
```

#### III. Decided Reason
To fix the bug, the bug should be changed that it compares ```p1``` and ```p2``` iterators. 
<br><br>

### 4.3. 410th patch - T1F 
#### I. Evaluated Result
```java
source/org/jfree/chart/util/ShapeUtilities.java: 274
-   PathIterator iterator1 = p1.getPathIterator(null);            
+   final PathIterator iterator1 = p2.getPathIterator(null); 
```

#### III. Fixed chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/util/ShapeUtilities.java: 274
final PathIterator iterator2 = p2.getPathIterator(null);
```
<br><br>


