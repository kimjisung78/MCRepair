# Lang 51
* <h4>Bug type: Type 2 (T1B / T1F, T2F)</h4>
* <h4>The number of chunks: 1 chunks (1 used chunk / 1 fixed chunks)</h4>
* <h4>The number of locations: 3 locations (1 used location / 1, 3 fixed locations)</h4>
<br>

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 670-684
    case 3: {
        char ch = str.charAt(0);
        if (ch == 'y') {
            return 
                (str.charAt(1) == 'e' || str.charAt(1) == 'E') &&
                (str.charAt(2) == 's' || str.charAt(2) == 'S');
        }
        if (ch == 'Y') {
            return 
                (str.charAt(1) == 'E' || str.charAt(1) == 'e') &&
                (str.charAt(2) == 'S' || str.charAt(2) == 's');
        }
+       return false;
    }
    case 4: {            
        char ch = str.charAt(0);
```
<br>

## 2. Used chunks and locations - T1B
* The number of used chunks: 1 chunk
* The number of used locations: 1 location
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 682
FAULT_OF_OMISSION
```
<br>

## 3. Correct combined patches per bug type
* T1F: 1, 5
* T2F: 98, 103, 112, 113
<br><br>

## 4. Examples of correct patches
### 4.1. 1st patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 682
+   return false;
    }
```

#### II. Fixed chunks and locations 
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 682
A location was inserted in front of Location 682.
```
<br><br>

### 4.2. 5th patch - T1F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 682
+   break;
    }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 1 location
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 682
A location was inserted in front of Location 682.
```

#### Decided Reason
To fix the bug, the bug must changed so that it prevents the fall through problem of ```case 3```.
<br><br>

### 4.3. 98th patch - T2F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 681
-   }
+   } else {
+       return false;
+   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 3 locations
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 681
} else {
    return false;
}
```

#### Decided Reason
To fix the bug, the bug must changed that it prevents the fall through problem of ```case 3```. Also, ```if (ch == 'Y')``` statement occurs the problem. Therefore, the statement must added else statement that prevents the problem.
<br><br>

### 4.4. 112nd patch - T2F
#### I. Fixed Result
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 681
-   }
+   } else {
+       break;
+   }
```

#### II. Fixed chunks and locations
* The number of fixed chunks: 1 chunk
* The number of fixed locations: 3 locations
```java
src/java/org/apache/commons/lang/BooleanUtils.java: 681
} else {
    break;
}
```

#### Decided Reason
Its reason is the same as the reason in the 98th patch.
<br><br>