# Closure 86
* <h4>Bug type: Type 2 (T1B / T1F, T2F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 3 locations (1 used location / 1, 3 fixed locations)</h4>
<br>

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

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
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

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
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

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2465
return false == true;
```

#### III. Explanation
```false == true``` is false.
<br><br>

### 4.3. 148th patch - T2F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2464-2465
-   case Token.NEW:
+   case Token.NEW:{
-       return true;
+       return false; 
+   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 3 locations
```java
src/com/google/javascript/jscomp/NodeUtil.java: 2464-2465
case Token.NEW:{
    return false;
}
```
<br><br>
