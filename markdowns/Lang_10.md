# Lang 10 - Type 3 (T3B / T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304-314
-   boolean wasWhite=false;
    for(int i= 0; i<value.length(); ++i) {
        char c= value.charAt(i);
-       if(Character.isWhitespace(c)) {
-           if(!wasWhite) {
-               wasWhite=true;
-               regex.append("\\s*+");
-           }
-           continue;
-       }
-       wasWhite= false;
```
<br>

## 2. Used chunks and locations - 2 chunks / 9 locations
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304
boolean wasWhite=false;
```

```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 307-314
if(Character.isWhitespace(c)) {
    if(!wasWhite) {
        wasWhite=true;
        regex.append("\\s*+");
    }
    continue;
}
wasWhite= false;
```
<br>

## 3. Correct combined patches per bug type
* T2F: 3
* T3F: 2, 5, 6, 250, 252
<br><br>

## 4. Examples of correct patches
### 4.1. 2nd patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304-314
-   boolean wasWhite=false;
+   boolean wasWhite=true;
    for(int i= 0; i<value.length(); ++i) {
        char c= value.charAt(i);
-       if(Character.isWhitespace(c)) {
-           if(!wasWhite) {
-               wasWhite=true;
-               regex.append("\\s*+");
-           }
-           continue;
-       }
-       wasWhite= false;
```

#### II. Fixed chunks and locations - 2 chunks / 9 locations
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304
boolean wasWhite=true;
```

```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 307-314
Location 307 was deleted.
Location 308 was deleted.
Location 309 was deleted.
Location 310 was deleted.
Location 311 was deleted.
Location 312 was deleted.
Location 313 was deleted.
Location 314 was deleted.
```

#### III. Decided Reason
Since ```boolean wasWhite``` variable is not called in its method, the varible is equivalent to the deletion.
<br><br>

### 4.2. 3rd patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304-314
    boolean wasWhite=false;
    for(int i= 0; i<value.length(); ++i) {
        char c= value.charAt(i);
-       if(Character.isWhitespace(c)) {
-           if(!wasWhite) {
-               wasWhite=true;
-               regex.append("\\s*+");
-           }
-           continue;
-       }
-       wasWhite= false;
```

#### II. Fixed chunks and locations - 1 chunk / 8 locations
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 307-314
Location 307 was deleted.
Location 308 was deleted.
Location 309 was deleted.
Location 310 was deleted.
Location 311 was deleted.
Location 312 was deleted.
Location 313 was deleted.
Location 314 was deleted.
```

#### III. Decided Reason
Its reason is the same as the reason in the 2nd patch.
<br><br>

### 4.3. 5th patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304-314
-   boolean wasWhite=false;
+   boolean white=false;
    for(int i= 0; i<value.length(); ++i) {
        char c= value.charAt(i);
-       if(Character.isWhitespace(c)) {
-           if(!wasWhite) {
-               wasWhite=true;
-               regex.append("\\s*+");
-           }
-           continue;
-       }
-       wasWhite= false;
```

#### II. Fixed chunks and locations - 2 chunks / 9 locations
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304
boolean white=false;
```

```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 307-314
Location 307 was deleted.
Location 308 was deleted.
Location 309 was deleted.
Location 310 was deleted.
Location 311 was deleted.
Location 312 was deleted.
Location 313 was deleted.
Location 314 was deleted.
```

#### III. Decided Reason
Since ```boolean wasWhite``` variable is not in its method, the varible is equivalent to the deletion.
<br><br>

### 4.4. 252th patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304-314
-   boolean wasWhite=false;
    for(int i= 0; i<value.length(); ++i) {
        char c= value.charAt(i);
-       if(Character.isWhitespace(c)) {
-           if(!wasWhite) {
-               wasWhite=true;
-               regex.append("\\s*+");
-           }
-           continue;
-       }
-       wasWhite= false;
```

#### II. Fixed chunks and locations - 2 chunks / 9 locations
```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 304
Location 304 was deleted.
```

```java
src/main/java/org/apache/commons/lang3/time/FastDateParser.java: 307-314
Location 307 was deleted.
Location 308 was deleted.
Location 309 was deleted.
Location 310 was deleted.
Location 311 was deleted.
Location 312 was deleted.
Location 313 was deleted.
Location 314 was deleted.
```
<br><br>