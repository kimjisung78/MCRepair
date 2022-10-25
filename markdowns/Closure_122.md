# Closure 122 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/parsing/IRFactory.java: 249-252
    * Check to see if the given block comment looks like it should be JSDoc.
    */
    private void handleBlockComment(Comment comment) {
+   Pattern p = Pattern.compile("(/|(\n[ \t]*))\\*[ \t]*@[a-zA-Z]");
-   if (comment.getValue().indexOf("/* @") != -1 || comment.getValue().indexOf("\n * @") != -1) {
+   if (p.matcher(comment.getValue()).find()) {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/parsing/IRFactory.java: 252
if (comment.getValue().indexOf("/* @") != -1 || comment.getValue().indexOf("\n * @") != -1) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 52
<br><br>

## 4. Examples of correct patches
### 4.1. 52th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/parsing/IRFactory.java: 252
-   if (comment.getValue().indexOf("/* @") != -1 || comment.getValue().indexOf("\n * @") != -1) {
+   if (comment.getValue().indexOf("/* @") != -1 || comment.getValue().indexOf("@") != -1) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/com/google/javascript/jscomp/parsing/IRFactory.java: 252
if (comment.getValue().indexOf("/* @") != -1 || comment.getValue().indexOf("@") != -1) {
```

#### III. Decided Reason
To fix the bug, ```if (comment.getValue().indexOf("/* @") != -1 || comment.getValue().indexOf("\n * @") != -1) {``` must changed that it must find comments that include ```@```, a character of comment.
<br><br>