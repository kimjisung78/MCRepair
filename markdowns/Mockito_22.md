# Mockito 22 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/org/mockito/internal/matchers/Equality.java: 12-20
    public static boolean areEqual(Object o1, Object o2) {
+       if (o1 == o2 ) {            
+           return true;
-       if (o1 == null || o2 == null) {
+       } else if (o1 == null || o2 == null) {
            return o1 == null && o2 == null;
        } else if (isArray(o1)) {
            return isArray(o2) && areArraysEqual(o1, o2);
        } else {
            return o1.equals(o2);
        }
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/org/mockito/internal/matchers/Equality.java: 13
if (o1 == null || o2 == null) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 420
<br><br>

## 4. Examples of correct patches
### 4.1. 420th patch - T1F
#### I. Fixed Result
```java
    public static boolean areEqual(Object o1, Object o2) {
+       try{
-       if (o1 == null || o2 == null) {
+       if (o1 == null) {
            return o1 == null && o2 == null;
        } else if (isArray(o1)) {
            return isArray(o2) && areArraysEqual(o1, o2);
        } else {
            return o1.equals(o2);
        }
+       } catch (Exception e) {
+           return true;
+       } 
    }
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/org/mockito/internal/matchers/Equality.java: 13
if (o1 == null) {
```

#### III. Decided Reason
If ```o1``` argument is null, ```o1.equals(o2)``` statement occurs RuntimeException due to null comparison problem. Therefore, the bug must be changed that it fisrt checks null about the argument. After the change, the bug does not occur any exceptions. Hence, the try-catch statement of the patch is dead and is not working. Also, the statement was not counted about the number of chunks and locations.
<br><br>