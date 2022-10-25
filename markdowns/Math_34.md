# Math 34 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/apache/commons/math3/genetics/ListPopulation.java: 208-210
    public Iterator<Chromosome> iterator() {
-       return chromosomes.iterator();
+       return getChromosomes().iterator();
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/genetics/ListPopulation.java: 209
return chromosomes.iterator();
```
<br>

## 3. Correct combined patches per bug type
* T1F: 70
<br><br>

## 4. Examples of correct patches
### 4.1. 70th patch - T1F
#### I. Fixed Result
```java
src/main/java/org/apache/commons/math3/genetics/ListPopulation.java: 209
-   return chromosomes.iterator();
+   return chromosomes.stream().iterator();
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/main/java/org/apache/commons/math3/genetics/ListPopulation.java: 209
return chromosomes.stream().iterator();
```

#### III. Decided Reason
To fix the bug, the bug must be changed that it returns iterator of ```chromosomes``` field.
<br><br>