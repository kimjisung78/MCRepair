# Closure 38
* <h4>Bug type: Type 1 (T1B / T1F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 1 location (1 used location / 1 fixed location)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/CodeConsumer.java: 244-247
    boolean negativeZero = isNegativeZero(x);
-   if (x < 0 && prev == '-') {
+   if ((x < 0 || negativeZero) && prev == '-') {
        add(" ");            
    }
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/com/google/javascript/jscomp/CodeConsumer.java: 245
if (x < 0 && prev == '-') {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 8, 11
<br><br>

## 4. Examples of correct patches
### 4.1. 8th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/CodeConsumer.java: 245
-   if ((x < 0 || negativeZero) && prev == '-') {
+   if (x <= 0 && prev == '-') {
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/com/google/javascript/jscomp/CodeConsumer.java: 245
if (x <= 0 && prev == '-') {
```

#### III. Decided Reason
```negativeZero``` indicates ```-0```. In Java, ```-0 == 0``` is true.
<br><br>

### 4.2. 11st patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/CodeConsumer.java: 245
-   if ((x < 0 || negativeZero) && prev == '-') {
+   if (x < 1 && prev == '-') {
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/com/google/javascript/jscomp/CodeConsumer.java: 245
if (x < 1 && prev == '-') {
```

#### III. Decided Reason
Its reason is the same as the reason in the 8th patch.
<br><br>