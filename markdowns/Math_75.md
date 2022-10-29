# Math 75
* <h4>Bug type: Type 1 (T1B / T1F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 1 location (1 used location / 1 fixed location)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/stat/Frequency.java: 303
-   return getCumPct((Comparable<?>) v);
+   return getPct((Comparable<?>) v);
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/main/java/org/apache/commons/math/stat/Frequency.java: 303
return getCumPct((Comparable<?>) v);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 8, 49, 76, 334, 353
<br><br>

## 4. Examples of correct patches
### 4.1. 8th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/stat/Frequency.java: 303
-   return getCumPct((Comparable<?>) v);
+   return getPct((Comparable<?>) v);
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/math/stat/Frequency.java: 303
return getPct((Comparable<?>) v);
```  
<br>

### 4.2. 76th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/stat/Frequency.java: 303
-   return getCumPct((Comparable<?>) v);
+   return getPct((Comparable) v);
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/math/stat/Frequency.java: 303
return getPct((Comparable) v);
```  
<br><br>