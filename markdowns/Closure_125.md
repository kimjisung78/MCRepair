# Closure 125 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1660-1663
    FunctionType fnType = type.toMaybeFunctionType();
-   if (fnType != null) {
+   if (fnType != null && fnType.hasInstanceType()) {
        visitParameterList(t, n, fnType);
        ensureTyped(t, n, fnType.getInstanceType());
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1661
if (fnType != null) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 251
<br><br>

## 4. Examples of correct patches
### 4.1. 251st patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1661
-   if (fnType != null) {
+   if (fnType != null && ! fnType.isNativeObjectType()) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1661
if (fnType != null && ! fnType.isNativeObjectType()) {
```

#### III. Decided Reason
```isNativeObjectType()``` method of ```FunctionType``` class indicates that the method do not include ```hasInstanceType()``` method of the class. Therefore, ```FunctionType``` class has been implemented as follows:
```java
src/com/google/javascript/rhino/jstype/FunctionType.java: 1142-1145
if (!isNativeObjectType()) {
    if (hasInstanceType()) {
        getInstanceType().clearCachedValues();
    }
```
<br><br>