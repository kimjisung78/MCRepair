# Lang 34
* <h4>Bug type: Type 3 (T3B / T1F, T3F)</h4>
* <h4>The number of chunks: 2 chunks (2 used chunks / 1, 2 fixed chunks)</h4>
* <h4>The number of locations: 2 locations (2 used locations / 1, 2 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 147-149
    static Map<Object, Object> getRegistry() {
-       return REGISTRY.get() != null ? REGISTRY.get() : Collections.<Object, Object>emptyMap();
+       return REGISTRY.get();
    }
```

```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 162-165
    static boolean isRegistered(Object value) {
        Map<Object, Object> m = getRegistry();
-       return m.containsKey(value);
+       return m != null && m.containsKey(value);
    }
```
<br>

## 2. Used chunks and locations - T3B
* The number of used chunks: 2 chunks
* The number of used locations: 2 locations
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 148
return REGISTRY.get() != null ? REGISTRY.get() : Collections.<Object, Object>emptyMap();
```

```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 164
return m.containsKey(value);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 33
* T3F: 2,033, 5,133, 6,933, 9,233
<br><br>

## 4. Examples of correct patches
### 4.1. 33rd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 164
-   return m.containsKey(value);
+   return m != null && m.containsKey(value);
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 164
return m != null && m.containsKey(value);
```
<br><br>

### 4.2. 2,033rd patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 148
-   return REGISTRY.get() != null ? REGISTRY.get() : Collections.<Object, Object>emptyMap();
+   return REGISTRY.get() != null ? REGISTRY.get() : Collections.emptyMap();
```

```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 164
-   return m.containsKey(value);
+   return m != null && m.containsKey(value);
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 148
return REGISTRY.get() != null ? REGISTRY.get() : Collections.emptyMap();
```

```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 164
return m != null && m.containsKey(value);
```
<br><br>

### 4.3. 9,233rd patch - T3F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 148
-   return REGISTRY.get() != null ? REGISTRY.get() : Collections.<Object, Object>emptyMap();
+   return REGISTRY.get();
```

```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 164
-   return m.containsKey(value);
+   return m != null && m.containsKey(value);
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 2 locations
```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 148
return REGISTRY.get();
```

```java
src/main/java/org/apache/commons/lang3/builder/ToStringStyle.java: 164
return m != null && m.containsKey(value);
```
<br><br>

