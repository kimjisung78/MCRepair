# Mockito 5 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/org/mockito/internal/verification/VerificationOverTimeImpl.java: 91
-   catch (org.mockito.exceptions.verification.junit.ArgumentsAreDifferent e) {
+   catch (AssertionError e) {
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/org/mockito/internal/verification/VerificationOverTimeImpl.java: 91
catch (org.mockito.exceptions.verification.junit.ArgumentsAreDifferent e) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 82
<br><br>

## 4. Examples of correct patches
### 4.1. 82nd patch - T1F
#### I. Fixed Result
```java
src/org/mockito/internal/verification/VerificationOverTimeImpl.java: 91
-   catch (org.mockito.exceptions.verification.junit.ArgumentsAreDifferent e) {
+   catch (AssertionError e) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/org/mockito/internal/verification/VerificationOverTimeImpl.java: 91
catch (AssertionError e) {
```
<br><br>