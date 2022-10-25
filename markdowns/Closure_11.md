# Closure 11 - Type 2 (T2B / T2F, T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1312-1315
    if (childType.isDict()) {
        report(t, property, TypeValidator.ILLEGAL_PROPERTY_ACCESS, "'.'", "dict");
-   } else if (n.getJSType() != null && parent.isAssign()) {
-       return;
```
<br>

## 2. Used chunks and locations - 1 chunk / 2 locations
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1314-1315
} else if (n.getJSType() != null && parent.isAssign()) {
return;
```
<br>

## 3. Correct combined patches per bug type
* T2F: 11
* T3F: 2
<br><br>

## 4. Examples of correct patches
### 4.1. 2nd patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1314-1315
-   } else if (n.getJSType() != null && parent.isAssign()) {            
-       return;
```

```java
src/com/google/javascript/jscomp/TypeCheck.java: 1320-1321
        ensureTyped(t, n);           
-       return;
    }
```

#### II. Fixed chunks and locations - 2 chunks / 3 locations
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1314-1315
Location 1314 was deleted.
Location 1315 was deleted.
```

```java
src/com/google/javascript/jscomp/TypeCheck.java: 1321
A location was inserted in front of location 1321.
```

#### III. Decided Reason
A ```void``` method is equivalent to a method that performs ```return;```.
<br><br>

### 4.2. 11st patch - T2F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1314-1315
-   } else if (n.getJSType() != null && parent.isAssign()) {            
-       return;
```

#### II. Fixed chunks and locations - 1 chunk / 2 locations
```java
src/com/google/javascript/jscomp/TypeCheck.java: 1314-1315
Location 1314 was deleted.
Location 1315 was deleted.
```
<br><br>