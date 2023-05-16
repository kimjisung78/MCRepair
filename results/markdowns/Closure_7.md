# Closure 7
* <h4>Bug type: Type 3 (T1B / T2F, T3F)</h4>
* <h4>The number of chunks: 2 chunks (1 used chunks / 1, 2 fixed chunks)</h4>
* <h4>The number of locations: 2 locations (1 used location / 2 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 610-618
    public JSType caseObjectType(ObjectType type) {
        if (value.equals("function")) {
            JSType ctorType = getNativeType(U2U_CONSTRUCTOR_TYPE);
-           return resultEqualsValue && ctorType.isSubtype(type) ? ctorType : null;
+           if (resultEqualsValue) {
                // Objects are restricted to "Function", subtypes are left
+               return ctorType.getGreatestSubtype(type);
+           } else {
                // Only filter out subtypes of "function"
+               return type.isSubtype(ctorType) ? null : type;
+           }
        }
        return matchesExpectation("object") ? type : null;
    }
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 613
return resultEqualsValue && ctorType.isSubtype(type) ? ctorType : null;
```
<br>

## 3. Correct combined patches per bug type
* T2F: 41
* T3F: 2
<br><br>

## 4. Examples of correct patches
### 4.1. 2nd patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 613-614
+       if (resultEqualsValue && ctorType.isSubtype(type)) {
        return resultEqualsValue && ctorType.isSubtype(type) ? ctorType : null;
+       }
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 613
A location was inserted in front of Location 613.
```

```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 614
A location was inserted in front of Location 614.
```

#### III. Explanation
To fix the bug, ```public JSType caseObjectType(ObjectType type)``` must be changed that it returns ```ctorType```, ```type```, or ```null```. The patch returned ```ctorType```, ```type```, or ```null```.
<br><br>

### 4.2. 41st patch - T2F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 613
-   return resultEqualsValue && ctorType.isSubtype(type) ? ctorType : null;
+   if (resultEqualsValue && ctorType.isSubtype(type))
+       return resultEqualsValue ? ctorType : null;
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 2 locations
```java
src/com/google/javascript/jscomp/type/ChainableReverseAbstractInterpreter.java: 613
if (resultEqualsValue && ctorType.isSubtype(type))
    return resultEqualsValue ? ctorType : null;
```

#### III. Explanation
Its reason is the same as the reason in the 2nd patch.
<br>
