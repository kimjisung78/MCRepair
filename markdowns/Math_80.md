# Math 80 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/linear/EigenDecompositionImpl.java: 1135
-   int j = 4 * n - 1;
+   int j = 4 * (n - 1);
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/linear/EigenDecompositionImpl.java: 1135
int j = 4 * n - 1;
```
<br>

## 3. Correct combined patches per bug type
* T1F: 32
<br><br>

## 4. Examples of correct patches
### 4.1. 32nd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/linear/EigenDecompositionImpl.java: 1135
-   int j = 4 * n - 1;
+   int j = 4 * (n - 1);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/linear/EigenDecompositionImpl.java: 1135
int j = 4 * (n - 1);
```  
<br><br>