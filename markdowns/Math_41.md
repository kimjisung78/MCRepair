# Math 41 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math/stat/descriptive/moment/Variance.java: 519-522
    double sumWts = 0;
-   for (int i = 0; i < weights.length; i++) {
+   for (int i = begin; i < begin + length; i++) {
        sumWts += weights[i];
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/stat/descriptive/moment/Variance.java: 520
for (int i = 0; i < weights.length; i++) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 52, 163
<br><br>

## 4. Examples of correct patches
### 4.1. 52th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/stat/descriptive/moment/Variance.java: 520
-   for (int i = 0; i < weights.length; i++) {
+   for (int i = begin; i < begin + length; i++) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/stat/descriptive/moment/Variance.java: 520
for (int i = begin; i < begin + length; i++) {
```
<br>

### 4.2. 163rd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math/stat/descriptive/moment/Variance.java: 520
-   for (int i = 0; i < weights.length; i++) {
+   for (int i = begin + 0; i < begin + length; i++) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math/stat/descriptive/moment/Variance.java: 520
for (int i = begin + 0; i < begin + length; i++) {
```
<br><br>