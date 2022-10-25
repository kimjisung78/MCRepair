# Time 17 - Type 3 (T3B / T3F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/main/java/org/joda/time/DateTimeZone.java: 1167-1179
-   long instantBefore = convertUTCToLocal(instant - 3 * DateTimeConstants.MILLIS_PER_HOUR);
+   long instantBefore = instant - 3 * DateTimeConstants.MILLIS_PER_HOUR;
-   long instantAfter = convertUTCToLocal(instant + 3 * DateTimeConstants.MILLIS_PER_HOUR);
+   long instantAfter = instant + 3 * DateTimeConstants.MILLIS_PER_HOUR;
+   long offsetBefore = getOffset(instantBefore);
+   long offsetAfter = getOffset(instantAfter);
-   if (instantBefore == instantAfter) {
+   if (offsetBefore <= offsetAfter) {
        return instant;  // not an overlap (less than is a gap, equal is normal case)
    }

    // work out range of instants that have duplicate local times
+   long diff = offsetBefore - offsetAfter;
-   long local = convertUTCToLocal(instant);
+   long transition = nextTransition(instantBefore);
+   long overlapStart = transition - diff;
+   long overlapEnd = transition + diff;
-   return convertLocalToUTC(local, false, earlierOrLater ? instantAfter : instantBefore);
+   if (instant < overlapStart || instant >= overlapEnd) {
+       return instant;  // not an overlap
+   }

    // calculate result
+   long afterStart = instant - overlapStart;
+   if (afterStart >= diff) {
        // currently in later offset
+       return earlierOrLater ? instant : instant - diff;
+   } else {
        // currently in earlier offset
+       return earlierOrLater ? instant + diff : instant;
+   }
```
<br>

## 2. Used chunks and locations - 2 chunks / 5 locations
```java
src/main/java/org/joda/time/DateTimeZone.java: 1167-1169
long instantBefore = convertUTCToLocal(instant - 3 * DateTimeConstants.MILLIS_PER_HOUR);
long instantAfter = convertUTCToLocal(instant + 3 * DateTimeConstants.MILLIS_PER_HOUR);
if (instantBefore == instantAfter) {
```

```java
src/main/java/org/joda/time/DateTimeZone.java: 1174-1175
long local = convertUTCToLocal(instant);
return convertLocalToUTC(local, false, earlierOrLater ? instantAfter : instantBefore);
```
<br>

## 3. Correct combined patches per bug type
* T1F: 52, 100
<br><br>

## 4. Examples of correct patches
### 4.1. 52nd patch - T1F
#### I. Fixed Result
```java
src/main/java/org/joda/time/DateTimeZone.java: 1167-1169
-   long instantBefore = convertUTCToLocal(instant - 3 * DateTimeConstants.MILLIS_PER_HOUR);
+   long instantBefore = instant - 3 * DateTimeConstants.MILLIS_PER_HOUR;
-   long instantAfter = convertUTCToLocal(instant + 3 * DateTimeConstants.MILLIS_PER_HOUR);
+   long instantAfter = instant + 3 * DateTimeConstants.MILLIS_PER_HOUR;
    if (instantBefore == instantAfter) {
```

#### II. Fixed chunks and locations - 1 chunk / 2 locations
```java
src/main/java/org/joda/time/DateTimeZone.java: 1167-1168
long instantAfter = instant - 3 * DateTimeConstants.MILLIS_PER_HOUR;
long instantAfter = instant + 3 * DateTimeConstants.MILLIS_PER_HOUR;
```

#### III. Decided Reason
To fix the bug, the bug should be changed that it compares two instants wihtout ```convertUTCToLocal``` method.
<br><br>