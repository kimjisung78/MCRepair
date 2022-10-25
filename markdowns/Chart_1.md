# Chart 1 - Type 3 (T1B / T1F, T2F, T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1796-1799
    CategoryDataset dataset = this.plot.getDataset(index);
-   if (dataset != null) {
+   if (dataset == null) {
        return result;
    }
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1797
if (dataset != null) {
```
<br>

## 3. Correct combined patches per bug type
* T1F: 14, 95, 105, 117, 119, 163, 175, 301, 327, 354
* T2F: 355
* T3F: 223
<br><br>

## 4. Examples of correct patches
### 4.1. 14th patch - T1F
#### I. Fixed Result
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1797
-   if (dataset != null) {
+   if (dataset == null) {
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1797
if (dataset == null) {
```
<br>

### 4.2. 223rd patch - T3F
#### I. Fixed Result
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1797-1799
-   if (dataset != null) {
+   if (dataset == null) {
        return result;
-   }
```

#### II. Fixed chunks and locations - 2 chunks / 2 locations
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1797
if (dataset == null)
```

```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1799
Location 1799 was deleted.
```
<br>

### 4.3. 355th patch - T2F
#### I. Fixed Result
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1797-1799
-   if (dataset != null) {
+   if (dataset == null) {
-       return result;
+       return null;
    }
```

#### II. Fixed chunks and locations - 1 chunk / 2 locations
```java
source/org/jfree/chart/renderer/category/AbstractCategoryItemRenderer.java: 1797-1798
if (dataset == null) {
    return null;
```
<br><br>