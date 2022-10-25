# Closure 19 - Type 2 (T1B / T1F, T2F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 172-176
+   case Token.THIS:
    // "this" references aren't currently modeled in the CFG.
+       break;

    default:
        throw new IllegalArgumentException("Node cannot be refined. \n" +
            node.toStringTree());
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 174
FAULT_OF_OMISSION
```
<br>

## 3. Correct combined patches per bug type
* T1F: 411
* T2F: 412
<br><br>

## 4. Examples of correct patches
### 4.1. 411st patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 175, 176-177 (Divided Locations)
    default:
+       throw new IllegalArgumentException("Node cannot be refined. \n" + node.toStringTree());
-       break;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 176-177 (Divided Locations)
break;
```

#### III. Decided Reason
```IllegalArgumentException``` indicates that a method has been passed an illegal or inappropriate argument. Therefore, to throw the exception is optional. In addition, the situation that the exception does not occur does not affect source code.
<br><br>

### 4.2. 412nd patch - T2F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 175, 176-177 (Divided Locations)
-   default:
-       break;
```

#### II. Fixed chunks and locations - 1 chunk / 2 locations
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 175, 176-177 (Divided Locations)
Location 175 was deleted.
Divided Locations 176 and 177 were deleted.
```

#### III. Decided Reason
Its reason is the same as the reason in the 411st patch.
<br><br>