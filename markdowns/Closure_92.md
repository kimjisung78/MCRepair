# Closure 92 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/ProcessClosurePrimitives.java: 789
-   int indexOfDot = namespace.indexOf('.');
+   int indexOfDot = namespace.lastIndexOf('.');
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/ProcessClosurePrimitives.java: 789
int indexOfDot = namespace.indexOf('.');
```
<br>

## 3. Correct combined patches per bug type
* T1F: 2
<br><br>

## 4. Examples of correct patches
### 4.1. 2nd patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/ProcessClosurePrimitives.java: 789
-   int indexOfDot = namespace.indexOf('.');
+   int indexOfDot = namespace.lastIndexOf('.');
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/ProcessClosurePrimitives.java: 789
int indexOfDot = namespace.lastIndexOf('.');
```
<br><br>