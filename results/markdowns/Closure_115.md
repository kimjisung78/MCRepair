# Closure 115
* <h4>Bug type: Type 3 (T3B / T3F)</h4>
* <h4>The number of chunks: 2 chunks (2 used chunks / 2 fixed chunks)</h4>
* <h4>The number of locations: 11 locations (11 used locations / 10, 11 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
-   boolean hasSideEffects = false;
-   if (block.hasChildren()) {
-       Preconditions.checkState(block.hasOneChild());
-       Node stmt = block.getFirstChild();
-       if (stmt.isReturn()) {
-           hasSideEffects = NodeUtil.mayHaveSideEffects(stmt.getFirstChild(), compiler);
-       }
-   }
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
-   if (hasSideEffects && NodeUtil.canBeSideEffected(cArg)) {
-       return CanInlineResult.NO;
-   }
```
<br>

## 2. Used chunks and locations - T3B
* The number of used chunks: 2 chunks
* The number of used locations: 11 locations
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
-   boolean hasSideEffects = false;
-   if (block.hasChildren()) {
-       Preconditions.checkState(block.hasOneChild());
-       Node stmt = block.getFirstChild();
-       if (stmt.isReturn()) {
-           hasSideEffects = NodeUtil.mayHaveSideEffects(stmt.getFirstChild(), compiler);
-       }
-   }
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
-   if (hasSideEffects && NodeUtil.canBeSideEffected(cArg)) {
-       return CanInlineResult.NO;
-   }
```
<br>

## 3. Correct combined patches per bug type
* T3F: 1, 2, 28, 64
<br><br>

## 4. Examples of correct patches
### 4.1. 1st patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
-   boolean hasSideEffects = false;
-   if (block.hasChildren()) {
-       Preconditions.checkState(block.hasOneChild());
-       Node stmt = block.getFirstChild();
-       if (stmt.isReturn()) {
-           hasSideEffects = NodeUtil.mayHaveSideEffects(stmt.getFirstChild(), compiler);
-       }
-   }
+   boolean hasSideEffects = block.hasChildren();
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
-   if (hasSideEffects && NodeUtil.canBeSideEffected(cArg)) {
-       return CanInlineResult.NO;
-   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 11 locations
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
boolean hasSideEffects = block.hasChildren();
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
Location 730 was deleted.
Location 731 was deleted.
Location 732 was deleted.
```

#### III. Explanation
Because ```boolean hasSideEffects``` variable is not called in its method, the varible is equivalent to its deletion.
<br><br>

### 4.2. 2nd patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
-   boolean hasSideEffects = false;
-   if (block.hasChildren()) {
-       Preconditions.checkState(block.hasOneChild());
-       Node stmt = block.getFirstChild();
-       if (stmt.isReturn()) {
-           hasSideEffects = NodeUtil.mayHaveSideEffects(stmt.getFirstChild(), compiler);
-       }
-   }
+   boolean hasSideEffects = block.hasOneChild();
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
-   if (hasSideEffects && NodeUtil.canBeSideEffected(cArg)) {
-       return CanInlineResult.NO;
-   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 11 locations
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
boolean hasSideEffects = block.hasOneChild();
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
Location 730 was deleted.
Location 731 was deleted.
Location 732 was deleted.
```

#### III. Explanation
Its reason is the same as the reason in the 1st patch.
<br><br>

### 4.3. 28th patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
-   boolean hasSideEffects = false;
-   if (block.hasChildren()) {
-       Preconditions.checkState(block.hasOneChild());
-       Node stmt = block.getFirstChild();
-       if (stmt.isReturn()) {
-           hasSideEffects = NodeUtil.mayHaveSideEffects(stmt.getFirstChild(), compiler);
-       }
-   }
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
-   if (hasSideEffects && NodeUtil.canBeSideEffected(cArg)) {
-       return CanInlineResult.NO;
-   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 11 locations
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
Location 697 was deleted.
Location 698 was deleted.
Location 699 was deleted.
Location 700 was deleted.
Location 701 was deleted.
Location 702 was deleted.
Location 703 was deleted.
Location 704 was deleted.
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
Location 730 was deleted.
Location 731 was deleted.
Location 732 was deleted.
```
<br>

### 4.4. 64th patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 697-704
    boolean hasSideEffects = false;
-   if (block.hasChildren()) {
-       Preconditions.checkState(block.hasOneChild());
-       Node stmt = block.getFirstChild();
-       if (stmt.isReturn()) {
-           hasSideEffects = NodeUtil.mayHaveSideEffects(stmt.getFirstChild(), compiler);
-       }
-   }
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
-   if (hasSideEffects && NodeUtil.canBeSideEffected(cArg)) {
-       return CanInlineResult.NO;
-   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 10 locations
```java
src/com/google/javascript/jscomp/FunctionInjector.java: 698-704
Location 698 was deleted.
Location 699 was deleted.
Location 700 was deleted.
Location 701 was deleted.
Location 702 was deleted.
Location 703 was deleted.
Location 704 was deleted.
```

```java
src/com/google/javascript/jscomp/FunctionInjector.java: 730-732
Location 730 was deleted.
Location 731 was deleted.
Location 732 was deleted.
```

#### III. Explanation
Its reason is the same as the reason in the 1st patch.
<br><br>