# Closure 109
* <h4>Bug type: Type 1 (T1B / T1F)</h4>
* <h4>The number of chunks: 1 chunk (1 used chunk / 1 fixed chunk)</h4>
* <h4>The number of locations: 1 location (1 used location / 1 fixed location)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/parsing/JsDocInfoParser.java: 1907-1909
    private Node parseContextTypeExpression(JsDocToken token) {
+       if (token == JsDocToken.QMARK) {
+           return newNode(Token.QMARK);
+       } else {
-           return parseTypeName(token);
+           return parseBasicTypeExpression(token);
+       }
    }
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/com/google/javascript/jscomp/parsing/JsDocInfoParser.java: 1908
return parseTypeName(token);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 11, 447
<br><br>

## 4. Examples of correct patches
### 4.1. 11st patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/parsing/JsDocInfoParser.java: 1908
-   return parseTypeName(token);
+   return parseTypeExpression(token);
```
<br>

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/com/google/javascript/jscomp/parsing/JsDocInfoParser.java: 1908
return parseTypeExpression(token);
```

#### III. Explanation
```parseTypeExpression(token)``` method already returns either ```newNode(Token.QMARK)``` of ```JsDocToken.QMARK``` or ```parseBasicTypeExpression(token)``.
<br>

### 4.2. 447th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/parsing/JsDocInfoParser.java: 1908
-   return parseTypeName(token);
+   return this.parseTypeExpression(token);
```
<br>

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/com/google/javascript/jscomp/parsing/JsDocInfoParser.java: 1908
return this.parseTypeExpression(token);
```

#### III. Explanation
Its reason is the same as the reason in the 11st patch.
<br><br>