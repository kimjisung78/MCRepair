# Mockito 22
* <h4>Bug type: Type 3 (T1B / T3F)</h4>
* <h4>The number of chunks: 2 chunks (1 used chunk / 2 fixed chunks)</h4>
* <h4>The number of locations: 5 locations (1 used location / 5 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/org/mockito/internal/matchers/Equality.java: 12-20
    public static boolean areEqual(Object o1, Object o2) {
+       if (o1 == o2) {            
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
* T3F: 419, 421
<br><br>

## 4. Examples of correct patches
### 4.1. 419th patch - T3F
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
+           return false;
+       } 
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 5 locations
```java
src/org/mockito/internal/matchers/Equality.java: 13
A location was inserted in front of Location 13.
if (o1 == null) {
```

```java
src/org/mockito/internal/matchers/Equality.java: 20
Three locations were inserted in front of Location 20.
```

#### III. Explanation
Each ```Exception``` is always semantically different. Because each exception occurs at another place, time, or circumstance, and its stacktrace are different. Therefore, the following testcase that checks the equality for the two exceptions is strange.
```java
test/org/mockito/internal/matchers/EqualityTest.java: 23-24
Object badequals = new BadEquals();
assertTrue(areEqual(badequals,badequals));
```

To fix the bug, the bug must be changed that it returns false when an exception occurs or exceptions are compared, using a try-catch statement. 
Furthermore, because the testcase of the eqaulity is very bad, Defects4J should change the testcase as follows.
```java
test/org/mockito/internal/matchers/EqualityTest.java: 23-24
Object badequals = new BadEquals();
assertFalse(areEqual(badequals,badequals));
```

In addition, If you want to check the equality on Mockito, you must write a testcase as follows.
```java
given(otherServiceMock.bar()).willThrow(new CustomException());

when(() -> customService.foo());

then(caughtException()).isInstanceOf(CustomException.class);
```
<br><br>