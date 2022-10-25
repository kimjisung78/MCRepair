# Closure 10 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 1416-1420
    if (recurse) {
-       return allResultsMatch(n, MAY_BE_STRING_PREDICATE);
+       return anyResultsMatch(n, MAY_BE_STRING_PREDICATE);
    } else {
        return mayBeStringHelper(n);
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 1417
return allResultsMatch(n, MAY_BE_STRING_PREDICATE);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 1, 176
<br><br>

## 4. Examples of correct patches
### 4.1. 1st patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NodeUtil.java: 1417
-   return allResultsMatch(n, MAY_BE_STRING_PREDICATE);
+   return anyResultsMatch(n, MAY_BE_STRING_PREDICATE);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 1417
return anyResultsMatch(n, MAY_BE_STRING_PREDICATE);
```
<br>

### 4.2. 176th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NodeUtil.java: 1417
-   return allResultsMatch(n, MAY_BE_STRING_PREDICATE);
+   return (anyResultsMatch(n, MAY_BE_STRING_PREDICATE));
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 1417
return (anyResultsMatch(n, MAY_BE_STRING_PREDICATE));
```
<br><br>