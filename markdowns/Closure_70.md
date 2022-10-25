# Closure 70 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/TypedScopeCreator.java: 1744-1746
    defineSlot(astParameter, functionNode,
-       jsDocParameter.getJSType(), true);
+       jsDocParameter.getJSType(), false);
    jsDocParameter = jsDocParameter.getNext();
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/TypedScopeCreator.java: 1744-1745 (Divided Locations)
defineSlot(astParameter, functionNode, jsDocParameter.getJSType(), true);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 37
<br><br>

## 4. Examples of correct patches
### 4.1. 37th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/TypedScopeCreator.java: 1744-1745 (Divided Locations)
-   defineSlot(astParameter, functionNode, jsDocParameter.getJSType(), false);
+   defineSlot(astParameter, functionNode, jsDocParameter.getJSType(), true);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/TypedScopeCreator.java: 1744-1745 (Divided Locations)
defineSlot(astParameter, functionNode, jsDocParameter.getJSType(), true);
```
<br><br>