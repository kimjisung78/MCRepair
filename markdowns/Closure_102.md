# Closure 102 - Type 3 (T3B / T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/Normalize.java: 88-94
    NodeTraversal.traverse(compiler, root, this);            
+   removeDuplicateDeclarations(root);            
    if (MAKE_LOCAL_NAMES_UNIQUE) {            
        MakeDeclaredNamesUnique renamer = new MakeDeclaredNamesUnique();            
        NodeTraversal t = new NodeTraversal(compiler, renamer);            
        t.traverseRoots(externs, root);            
    }            
-   removeDuplicateDeclarations(root);
```
<br>

## 2. Used chunks and locations - 2 chunks / 2 locations
```java
src/com/google/javascript/jscomp/Normalize.java: 89
FAULT_OF_OMISSION
```

```java
src/com/google/javascript/jscomp/Normalize.java: 94
removeDuplicateDeclarations(root);
```
<br>

## 3. Correct combined patches per bug type
* T3F: 1, 42, 355
<br><br>

## 4. Examples of correct patches
### 4.1. 1st patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/Normalize.java: 86-97
    @Override            
    public void process(Node externs, Node root) {
        NodeTraversal.traverse(compiler, root, this);
+       removeDuplicateDeclarations(root);
        if (MAKE_LOCAL_NAMES_UNIQUE) {
            MakeDeclaredNamesUnique renamer = new MakeDeclaredNamesUnique();
            NodeTraversal t = new NodeTraversal(compiler, renamer);
            t.traverseRoots(externs, root);
        }
-       removeDuplicateDeclarations(root);
        new PropogateConstantAnnotations(compiler, assertOnChange)
            .process(externs, root);
    }
```

#### II. Fixed chunks and locations - 2 chunks / 2 locations
```java
src/com/google/javascript/jscomp/Normalize.java: 89
A location was inserted in front of Location 89.
```

```java
src/com/google/javascript/jscomp/Normalize.java: 94
Location 94 was deleted.
```
<br>

### 4.2. 355th patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/Normalize.java: 88-94
    NodeTraversal.traverse(compiler, root, this);            
+   removeDuplicateDeclarations(root);            
    if (MAKE_LOCAL_NAMES_UNIQUE) {            
        MakeDeclaredNamesUnique renamer = new MakeDeclaredNamesUnique();            
        NodeTraversal t = new NodeTraversal(compiler, renamer);            
        t.traverseRoots(externs, root);            
    }            
-   removeDuplicateDeclarations(root);
```

```java
src/com/google/javascript/jscomp/Normalize.java: 95-97
        new PropogateConstantAnnotations(compiler, assertOnChange)            
            .process(externs, root);
+   return;
    }
```

#### II. Fixed chunks and locations - 2 chunks / 3 locations
```java
src/com/google/javascript/jscomp/Normalize.java: 89
A location was inserted in front of Location 89.
```

```java
src/com/google/javascript/jscomp/Normalize.java: 94
Location 94 was deleted.
```

```java
src/com/google/javascript/jscomp/Normalize.java: 97
A location was inserted in front of Location 97.
```

#### III. Decided Reason
A ```void``` method is equivalent to a method that performs ```return;```.
<br><br>