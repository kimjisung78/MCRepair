# Closure 40
* <h4>Bug type: Type 3 (T3B / T1F, T3F)</h4>
* <h4>The number of chunks: 2 chunks (2 used chunks / 1, 2 fixed chunks)</h4>
* <h4>The number of locations: 3 locations (3 used locations / 1, 3 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 633-640
    NameInformation ns = createNameInformation(t, nameNode, n);
    if (ns != null && ns.onlyAffectsClassDef) {
-       JsName name = getName(ns.name, false);
+       JsName name = getName(ns.name, true);
-       if (name != null) {
            refNodes.add(new ClassDefiningFunctionNode(
                name, n, parent, parent.getParent()));
-        }
    }
```
<br>

## 2. Used chunks and locations - T3B
* The number of used chunks: 2 chunks
* The number of used locations: 3 locations
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 635-636
JsName name = getName(ns.name, false);
if (name != null) {
```

```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 639
}
```
<br>

## 3. Correct combined patches per bug type
* T1F: 80
* T3F: 37, 44, 230, 276, 365, 378
<br><br>

## 4. Examples of correct patches
### 4.1. 37th patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 635-639
-   JsName name = getName(ns.name, false);
+   JsName name = getName(ns.name, true);
-   if (name != null) {
+   if (name != null)
        refNodes.add(new ClassDefiningFunctionNode(
            name, n, parent, parent.getParent()));
-   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 3 locations
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 635-636
JsName name = getName(ns.name, true);
if (name != null)
```

```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 639
Location 639 was deleted.
```

#### III. Decided Reason
```getName(ns.name, true)``` returns the name of ````ns.name`` after null-cheking.
<br><br>

### 4.2. 80th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 635-639
-   JsName name = getName(ns.name, false);
+   JsName name = getName(ns.name, true);
    if (name != null) {
        refNodes.add(new ClassDefiningFunctionNode(
            name, n, parent, parent.getParent()));
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 635
JsName name = getName(ns.name, true);
```

#### III. Decided Reason
Its reason is the same as the reason in the 37th patch.
<br><br>

### 4.3. 276th patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 635-639
-   JsName name = getName(ns.name, false);
+   JsName name = getName(ns.name, true);
-   if (name != null) {
        refNodes.add(new ClassDefiningFunctionNode(
            name, n, parent, parent.getParent()));
-   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 3 locations
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 635-636
JsName name = getName(ns.name, true);
Location 636 was deleted.
```

```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 639
Location 639 was deleted.
```
<br><br>