# Closure 115 - Type 3 (T3B / T3F)

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

## 2. Used chunks and locations - 2 chunks / 11 locations
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

#### II. Fixed chunks and locations - 2 chunks / 11 locations
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

#### III. Decided Reason
Since ```boolean hasSideEffects``` variable is not called in its method, the varible is equivalent to the deletion.
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

#### II. Fixed chunks and locations - 2 chunks / 11 locations
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

#### III. Decided Reason
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

#### II. Fixed chunks and locations - 2 chunks / 11 locations
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

#### II. Fixed chunks and locations - 2 chunks / 10 locations
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

#### III. Decided Reason
Its reason is the same as the reason in the 1st patch.
<br><br>