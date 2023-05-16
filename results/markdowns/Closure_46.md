# Closure 46
* <h4>Bug type: Type 3 (T2B / T2F, T3F)</h4>
* <h4>The number of chunks: 3 chunks (1 used chunks / 1, 2, 3 fixed chunks)</h4>
* <h4>The number of locations: 13 locations (13 used locations / 9, 10, 13 fixed locations)</h4>
<br>

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

## 2. Used chunks and locations - T2B
* The number of used chunks: 1 chunk
* The number of used locations: 13 locations
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
<br>

## 3. Correct combined patches per bug type
* T2F: 415, 423
* T3F: 402, 403
<br><br>

## 4. Examples of correct patches
### 4.1. 402nd patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 140-155
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

#### II. Fixed chunks and locations
* The number of fixed chunks: 2 chunks
* The number of fixed locations: 9 locations
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 142
Location 142 was deleted.
```

```java
src/com/google/javascript/rhino/jstype/RecordType.java: 144-146, 147-149 (Divided Locations), 150-151 (Divided Locations), 152-154
Location 144 was deleted.
Location 145 was deleted.
Location 146 was deleted.
Locations 147, 148, and 149 were deleted.
Locations 150 and 151 were deleted.
Location 152 was deleted.
Location 153 was deleted.
Location 154 was deleted.
```

#### III. Explanation
To only return ```super.getLeastSupertype(that)``` in ```public JSType getLeastSupertype(JSType that)``` is equivalent to the deletion of the method.
<br><br>

### 4.2. 403rd patch - T3F
#### I. Fixed Result
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 140-155
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

#### II. Fixed chunks and locations
* The number of fixed chunks: 3 chunks
* The number of fixed locations: 10 locations
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 140
Location 140 was deleted.
```

```java
src/com/google/javascript/rhino/jstype/RecordType.java: 142
Location 142 was deleted.
```

```java
src/com/google/javascript/rhino/jstype/RecordType.java: 144-146, 147-149 (Divided Locations), 150-151 (Divided Locations), 152-154
Location 144 was deleted.
Location 145 was deleted.
Location 146 was deleted.
Locations 147, 148, and 149 were deleted.
Locations 150 and 151 were deleted.
Location 152 was deleted.
Location 153 was deleted.
Location 154 was deleted.
```

#### III. Explanation
Its reason is the same as the reason in the 402nd patch.
<br><br>

### 4.3. 423rd patch - T2F
#### I. Fixed Result
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 140-155
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

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 13 locations
```java
src/com/google/javascript/rhino/jstype/RecordType.java: 140-146, 147-149 (Divided Locations), 150-151 (Divided Locations), 152-155
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
