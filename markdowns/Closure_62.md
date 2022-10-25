# Closure 62 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/LightweightMessageFormatter.java: 97-101
    if (excerpt.equals(LINE)
-       && 0 <= charno && charno < sourceExcerpt.length()) {
+       && 0 <= charno && charno <= sourceExcerpt.length()) {
    for (int i = 0; i < charno; i++) {
        char c = sourceExcerpt.charAt(i);
        if (Character.isWhitespace(c)) {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/LightweightMessageFormatter.java: 97-98 (Divided Locations)
if (excerpt.equals(LINE) && 0 <= charno && charno < sourceExcerpt.length()) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 14
<br><br>

## 4. Examples of correct patches
### 4.1. 14th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/LightweightMessageFormatter.java: 97-98 (Divided Locations)
-   if (excerpt.equals(LINE) && 0 <= charno && charno < sourceExcerpt.length()) {
+   if (excerpt.equals(LINE) && 0 <= charno && charno <= sourceExcerpt.length()) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/ClosureCodingConvention.java: 97-98 (Divided Locations)
if (excerpt.equals(LINE) && 0 <= charno && charno <= sourceExcerpt.length()) {
```
<br><br>