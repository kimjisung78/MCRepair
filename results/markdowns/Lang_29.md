# Lang 29
* <h4>Bug type: Type 1 (T1B / T1F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 1 location (1 used location / 1 fixed location)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/lang3/SystemUtils.java: 1672-1674
-   static float toJavaVersionInt(String version) {
+   static int toJavaVersionInt(String version) {
        return toVersionInt(toJavaVersionIntArray(version, JAVA_VERSION_TRIM_SIZE));
    }
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/main/java/org/apache/commons/lang3/SystemUtils.java: 1672
static float toJavaVersionInt(String version) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 2
<br><br>

## 4. Examples of correct patches
### 4.1. 2nd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/SystemUtils.java: 1672
-   static float toJavaVersionInt(String version) {
+   static int toJavaVersionInt(String version) {
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/lang3/SystemUtils.java: 1672
static int toJavaVersionInt(String version) {
```

#### III. Explanation
Although the bug had correct patches in its patch space, its evaluated result was CO (Compilable). Because the bug has had [this problem](https://github.com/rjust/defects4j/issues/481), Defects4J must address the problem.
<br><br>