# Closure 38 - Type 1 (T1B / T1F)

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

## 2. Used chunks and locations - 1 chunk / 1 location
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

#### II. Fixed chunks and locations - 1 chunk / 1 location
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

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/CodeConsumer.java: 245
if (x < 1 && prev == '-') {
```

#### III. Decided Reason
Its reason is the same as the reason in the 8th patch.
<br><br>