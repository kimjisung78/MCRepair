# Closure 86 - Type 1 (T1B / T1F, T2F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2461-2466
    case Token.NEW:
        // TODO(nicksantos): This needs to be changed so that it
        // returns true iff we're sure the value was never aliased from inside
        // the constructor (similar to callHasLocalResult)
-       return true;
+       return false;
    case Token.FUNCTION:
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2465
return true;
```
<br>

## 3. Correct combined patches per bug type
* T1F: 84, 137, 164
* T2F: 148
<br><br>

## 4. Examples of correct patches
### 4.1. 84th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2465
-   return true;
+   return false;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2465
return false;
```
<br>

### 4.2. 137th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2465
-   return true;
+   return false == true;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2465
return false == true;
```

#### III. Decided Reason
```false == true``` is false.
<br><br>

### 4.1. 148th patch - T2F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2464-2465
-   case Token.NEW:
+   case Token.NEW:{
-       return true;
+       return false; 
+   }
```

#### II. Fixed chunks and locations - 1 chunk / 3 locations
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2464-2465
case Token.NEW:{
    return false;
}
```
<br><br>