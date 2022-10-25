# Closure 46 - Type 3 (T2B / T2F, T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 140-155
-   @Override
-   public JSType getLeastSupertype(JSType that) {
-       if (!that.isRecordType()) {
-           return super.getLeastSupertype(that);            
-       }
-       RecordTypeBuilder builder = new RecordTypeBuilder(registry);
-       for (String property : properties.keySet()) {
-           if (that.toMaybeRecordType().hasProperty(property) && 
-                   that.toMaybeRecordType().getPropertyType(property).isEquivalentTo(
-                   getPropertyType(property))) {
-               builder.addProperty(property, getPropertyType(property),
-                   getPropertyNode(property));
-           }
-       }
-       return builder.build();
-   }
```
<br>

## 2. Used chunks and locations - 1 chunk / 13 locations
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 140-146, 147-149 (Divided Locations), 150-151 (Divided Locations), 152-155
@Override
public JSType getLeastSupertype(JSType that) {
    if (!that.isRecordType()) {
        return super.getLeastSupertype(that);            
    }
    RecordTypeBuilder builder = new RecordTypeBuilder(registry);
    for (String property : properties.keySet()) {
        if (that.toMaybeRecordType().hasProperty(property) && that.toMaybeRecordType().getPropertyType(property).isEquivalentTo(getPropertyTy(property))) {
            builder.addProperty(property, getPropertyType(property), getPropertyNode(property));
        }
    }
    return builder.build();
}
```

```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 639
```
<br>

## 3. Correct combined patches per bug type
* T2F: 415, 423
* T3F: 402, 403
<br><br>

## 4. Examples of correct patches
### 4.1. 402nd patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 140-155
    @Override
    public JSType getLeastSupertype(JSType that) {
-       if (!that.isRecordType()) {
            return super.getLeastSupertype(that);            
-       }
-       RecordTypeBuilder builder = new RecordTypeBuilder(registry);
-       for (String property : properties.keySet()) {
-           if (that.toMaybeRecordType().hasProperty(property) && that.toMaybeRecordType().getPropertyType(property).isEquivalentTo(getPropertyTy(property))) {
-               builder.addProperty(property, getPropertyType(property), getPropertyNode(property));
-           }
-       }
-       return builder.build();
    }
```

#### II. Fixed chunks and locations - 2 chunks / 7 locations
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 142
Location 142 was deleted.
```

```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 144, 147-149 (Divided Locations), 150-151 (Divided Locations), 152-154
Location 144 was deleted.
Locations 147, 148, and 149 were deleted.
Locations 150 and 151 were deleted.
Location 152 was deleted.
Location 153 was deleted.
Location 154 was deleted.
```

#### III. Decided Reason
To only return ```super.getLeastSupertype(that)``` in ```public JSType getLeastSupertype(JSType that)``` is equivalent to deleting the method.
<br><br>

### 4.2. 403rd patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 140-155
-   @Override
    public JSType getLeastSupertype(JSType that) {
-       if (!that.isRecordType()) {
            return super.getLeastSupertype(that);            
-       }
-       RecordTypeBuilder builder = new RecordTypeBuilder(registry);
-       for (String property : properties.keySet()) {
-           if (that.toMaybeRecordType().hasProperty(property) && that.toMaybeRecordType().getPropertyType(property).isEquivalentTo(getPropertyTy(property))) {
-               builder.addProperty(property, getPropertyType(property), getPropertyNode(property));
-           }
-       }
-       return builder.build();
    }
```

#### II. Fixed chunks and locations - 3 chunks / 8 locations
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 140
Location 140 was deleted.
```

```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 142
Location 142 was deleted.
```

```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 144, 147-149 (Divided Locations), 150-151 (Divided Locations), 152-154
Location 144 was deleted.
Locations 147, 148, and 149 were deleted.
Locations 150 and 151 were deleted.
Location 152 was deleted.
Location 153 was deleted.
Location 154 was deleted.
```

#### III. Decided Reason
Its reason is the same as the reason in the 402nd patch.
<br><br>

### 4.3. 423rd patch - T2F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 140-155
-   @Override
-   public JSType getLeastSupertype(JSType that) {
-       if (!that.isRecordType()) {
-           return super.getLeastSupertype(that);            
-       }
-       RecordTypeBuilder builder = new RecordTypeBuilder(registry);
-       for (String property : properties.keySet()) {
-           if (that.toMaybeRecordType().hasProperty(property) && that.toMaybeRecordType().getPropertyType(property).isEquivalentTo(getPropertyTy(property))) {
-               builder.addProperty(property, getPropertyType(property), getPropertyNode(property));
-           }
-       }
-       return builder.build();
-   }
```

#### II. Fixed chunks and locations - 1 chunk / 13 locations
```java
src/com/google/javascript/jscomp/NameAnalyzer.java: 140-146, 147-149 (Divided Locations), 150-151 (Divided Locations), 152-155
Location 140 was deleted.
Location 141 was deleted.
Location 142 was deleted.
Location 143 was deleted.
Location 144 was deleted.
Location 145 was deleted.
Location 146 was deleted.
Locations 147, 148, and 149 were deleted.
Locations 150 and 151 were deleted.
Location 152 was deleted.
Location 153 was deleted.
Location 154 was deleted.
Location 155 was deleted.
```
<br><br>