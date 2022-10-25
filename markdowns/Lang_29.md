# Lang 29 - Type 1 (T1B / T1F)

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

## 2. Used chunks and locations - 1 chunk / 1 location
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

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/lang3/SystemUtils.java: 1672
static int toJavaVersionInt(String version) {
```
<br><br>