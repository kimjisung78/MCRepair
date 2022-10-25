# Chart 20 - Type 1 (T1B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
source/org/jfree/chart/plot/ValueMarker.java: 93-97
    public ValueMarker(double value, Paint paint, Stroke stroke,
            Paint outlinePaint, Stroke outlineStroke, float alpha) {
-       super(paint, stroke, paint, stroke, alpha);
+       super(paint, stroke, outlinePaint, outlineStroke, alpha);
        this.value = value;
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/plot/ValueMarker.java: 95
super(paint, stroke, paint, stroke, alpha);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 188
<br><br>

## 4. Examples of correct patches
### 4.1. 188th patch - T1F
#### I. Fixed Result
```java
source/org/jfree/chart/plot/ValueMarker.java: 95
-   super(paint, stroke, paint, stroke, alpha);            
+   super(paint, stroke, outlinePaint, outlineStroke, alpha);
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/plot/ValueMarker.java: 95
super(paint, stroke, outlinePaint, outlineStroke, alpha);
```
<br><br>


