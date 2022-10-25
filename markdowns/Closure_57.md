# Closure 57 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/ClosureCodingConvention.java: 195-200
    if (functionName.equals(qualifiedName)) {
        Node target = callee.getNext();
-       if (target != null) {
+       if (target != null && target.getType() == Token.STRING) {
            className = target.getString();
        }
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/ClosureCodingConvention.java: 197
if (target != null) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 341
<br><br>

## 4. Examples of correct patches
### 4.1. 341st patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/ClosureCodingConvention.java: 196-199           
    Node target = callee.getNext();
-   if (target != null) {
+   if (target != null && target.getType() == Token.STRING) {
        className = target.getString();
    }
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/ClosureCodingConvention.java: 197
if (target != null && target.getType() == Token.STRING) {
```
<br><br>