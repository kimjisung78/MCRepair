# Mockito 22
* <h4>Bug type: Type 1 (T1B / T1F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 1 location (1 used location / 1 fixed location)</h4>
<br>

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

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
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

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/org/mockito/internal/matchers/Equality.java: 13
if (o1 == null) {
```

#### III. Decided Reason
If ```o1``` argument is null, ```o1.equals(o2)``` statement occurs RuntimeException due to null comparison problem. Therefore, the bug must be changed that it fisrt checks null about the argument. After the change, the bug does not occur any exceptions. Hence, the try-catch statement of the patch is dead and is not working. Also, the statement was not counted about the number of chunks and locations.
<br><br>