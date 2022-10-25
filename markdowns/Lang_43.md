# Lang 43 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/lang/text/ExtendedMessageFormat.java: 421-423
    if (escapingOn && c[start] == QUOTE) {
+       next(pos);
        return appendTo == null ? null : appendTo.append(QUOTE);
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/text/ExtendedMessageFormat.java: 422
FAULT_OF_OMISSION
```
<br>

## 3. Correct combined patches per bug type
* T1F: 4
<br><br>

## 4. Examples of correct patches
### 4.1. 4th patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/text/ExtendedMessageFormat.java: 422
+   next(pos);
    return appendTo == null ? null : appendTo.append(QUOTE);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/text/ExtendedMessageFormat.java: 422
A location was inserted in front of Location 422.
```
<br><br>