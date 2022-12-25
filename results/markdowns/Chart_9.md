# Chart 9
* <h4>Bug type: Type 1 (T1B / T1F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 1 location (1 used location / 1 fixed location)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
source/org/jfree/data/time/TimeSeries.java: 944-946
-   if (endIndex < 0) {
+   if ((endIndex < 0) || (endIndex < startIndex)) {
        emptyRange = true;
    }
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
source/org/jfree/data/time/TimeSeries.java: 944
if (endIndex < 0) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 36, 174, 388
<br><br>

## 4. Examples of correct patches
### 4.1. 36th patch - T1F
#### I. Fixed Result
```java
source/org/jfree/data/time/TimeSeries.java: 944
-   if (endIndex < 0) {
+   if (endIndex - startIndex < 0) {
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
source/org/jfree/data/time/TimeSeries.java: 944
if (endIndex - startIndex < 0) {
```

#### III. Explanation
To fix the bug, location 944 should be changed that ```endIndex``` is less than ```startIndex```. Therefore, ```if (endIndex - startIndex < 0) {``` is equivalent to ```if (endIndex < startIndex) {```.
<br><br>

### 4.2. 174th patch - T1F
#### I. Fixed Result
```java
source/org/jfree/data/time/TimeSeries.java: 944
-   if (endIndex < 0) {
+   if (endIndex < startIndex) {
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
source/org/jfree/data/time/TimeSeries.java: 944
if (endIndex < startIndex) {
```

#### III. Explanation
Its reason is the same as the reason in the 36th patch.
<br><br>

### 4.3. 388th patch - T1F
#### I. Fixed Result
```java
source/org/jfree/data/time/TimeSeries.java: 944
-   if (endIndex < 0) {
+   if (endIndex < 0 || endIndex < startIndex) {
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
source/org/jfree/data/time/TimeSeries.java: 944
if (endIndex < 0 || endIndex < startIndex) {
```
<br><br>