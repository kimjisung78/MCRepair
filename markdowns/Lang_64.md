# Lang 64 - Type 1 (T3B / T1F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/lang/enums/ValuedEnum.java: 182-184
    public int compareTo(Object other) {            
+       if (other == this) {            
+           return 0;            
+       }            
+       if (other.getClass() != this.getClass()) {            
+           if (other.getClass().getName().equals(this.getClass().getName())) {            
+               return iValue - getValueInOtherClassLoader(other);            
+           }            
+           throw new ClassCastException(            
+               "Different enum class '" + ClassUtils.getShortClassName(other.getClass()) + "'");            
+       }            
        return iValue - ((ValuedEnum) other).iValue;            
    }
```

```java
src/java/org/apache/commons/lang/enums/ValuedEnum.java: 189-196
    * @param other  the object to determine the value for
    * @return the value
    */
+   private int getValueInOtherClassLoader(Object other) {
+       try {
+           Method mth = other.getClass().getMethod("getValue", null);
+           Integer value = (Integer) mth.invoke(other, null);
+           return value.intValue();
+       } catch (NoSuchMethodException e) {
            // ignore - should never happen
+       } catch (IllegalAccessException e) {
            // ignore - should never happen
+       } catch (InvocationTargetException e) {
            // ignore - should never happen
+       }
+       throw new IllegalStateException("This should not happen");
+   }

    /**
```
<br>

## 2. Used chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/enums/ValuedEnum.java: 183
return iValue - ((ValuedEnum) other).iValue;
```

```java
src/java/org/apache/commons/lang/enums/ValuedEnum.java: 195
FAULT_OF_OMISSION
```
* Location 195 is a blank location related to "FAULT_OF_OMISSION". 
<br><br>

## 3. Correct combined patches per bug type
* T1F: 60
<br><br>

## 4. Examples of correct patches
### 4.1. 60th patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/enums/ValuedEnum.java: 183
+   super.compareTo(other);
    return iValue - ((ValuedEnum) other).iValue;
```

#### II. Fixed chunks and locations - 1 chunk / 1 location
```java
src/java/org/apache/commons/lang/enums/ValuedEnum.java: 183
A location was inserted in front of Location 183.
```

#### III. Decided Reason
To fix the bug, the bug must check ```Object other``` argument. Also, ```super.compareTo(other)``` method (```compareTo(other)``` method of ```Enum``` abstract class) already checks the argument the same as its developer's patch as follows:
```java
public int compareTo(Object other) {
    if (other == this) {
        return 0;
    }
    if (other.getClass() != this.getClass()) {
        if (other.getClass().getName().equals(this.getClass().getName())) {
            return iName.compareTo(getNameInOtherClassLoader(other));
        }
    }
    return iName.compareTo(((Enum) other).iName);
}
```
<br><br>