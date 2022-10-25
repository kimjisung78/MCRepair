# Math 104 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/math/special/Gamma.java: 37
-   private static final double DEFAULT_EPSILON = 10e-9;            
+   private static final double DEFAULT_EPSILON = 10e-15;
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/math/special/Gamma.java: 37
private static final double DEFAULT_EPSILON = 10e-9;
```
<br>

## 3. Correct combined patches per bug type
* T1F: 32, 57, 93, 96
<br><br>

## 4. Examples of correct patches
### 4.1. 32nd patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/math/special/Gamma.java: 37
-   private static final double DEFAULT_EPSILON = 10e-9;            
+   private static final double DEFAULT_EPSILON = 10e-15;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/math/special/Gamma.java: 37
private static final double DEFAULT_EPSILON = 10e-15;
```  
<br>

### 4.2. 57th patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/math/special/Gamma.java: 37
-   private static final double DEFAULT_EPSILON = 10e-9;            
+   private static final double DEFAULT_EPSILON = 10e-18;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/math/special/Gamma.java: 37
private static final double DEFAULT_EPSILON = 10e-18;
```

#### III. Decided Reason
To fix the bug, ```DEFAULT_EPSILON``` field is greater than ```10e-9```.
<br><br>