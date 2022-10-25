# Math 57 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
-   int sum=0;
+   double sum=0;
```               
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
double sum=0;
```
<br>

## 3. Correct combined patches per bug type
* T1F: 95, 101, 244
<br><br>

## 4. Examples of correct patches
### 4.1. 95th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
-   int sum=0;
+   double sum=0;
```  

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
double sum=0;
```  
<br>

### 4.2. 101st patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
-   int sum=0;
+   float sum=0;
```  

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
float sum=0;
```  
<br>

### 4.3. 244th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
-   int sum=0;
+   double sum=0.0;
```  

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/stat/clustering/KMeansPlusPlusClusterer.java: 175
double sum=0.0;
```  
<br><br>