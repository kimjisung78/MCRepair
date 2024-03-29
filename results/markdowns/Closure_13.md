# Closure 13
* <h4>Bug type: Type 3 (T3B / T3F)</h4>
* <h4>The number of chunks: 3 chunks (2 used chunks / 2, 3 fixed chunks)</h4>
* <h4>The number of locations: 3 locations (2 used locations / 2, 3 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 124-129
    Node c = node.getFirstChild();
        while(c != null) {
-       traverse(c);
        Node next = c.getNext();
+       traverse(c);
        c = next;
    }
```
<br>

## 2. Used chunks and locations - T3B
* The number of used chunks: 2 chunks
* The number of used locations: 2 locations
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 126
traverse(c);
```

```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 128
FAULT_OF_OMISSION
```
<br>

## 3. Correct combined patches per bug type
* T3F: 194, 310
<br><br>

## 4. Examples of correct patches
### 4.1. 194th patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 124-129
    Node c = node.getFirstChild();
        while(c != null) {
-       traverse(c);
        Node next = c.getNext();
+       traverse(c);
        c = next;
    }
```

```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 137-138
        exitNode(node);
+   return;           
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 3 chunks
* The number of fixed locations: 3 locations
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 126
Location 126 was deleted.
```

```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 128
A location was inserted in front of Location 128.
```

```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 138
A location was inserted in front of Location 138.
```

#### III. Explanation
A ```void``` method is equivalent to a method that performs ```return;```.
<br><br>

### 4.2. 310th patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 124-129
    Node c = node.getFirstChild();
        while(c != null) {
-       traverse(c);
        Node next = c.getNext();
+       traverse(c);
        c = next;
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 126
Location 126 was deleted.
```

```java
src/com/google/javascript/jscomp/PeepholeOptimizationsPass.java: 128
A location was inserted in front of Location 128.
```
<br><br>