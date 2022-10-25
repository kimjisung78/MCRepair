# Closure 101 - Type 2 (T1B / T2F)

## 1. Developer's patch
* `-`: A fixed and deleted location
* `+`: A fixed and added location
```java
src/com/google/javascript/jscomp/CommandLineRunner.java: 430-438
    for (FormattingOption formattingOption : flags.formatting) {
        formattingOption.applyToOptions(options);
    }
-   if (flags.process_closure_primitives) {
-       options.closurePass = true;
-   }

+   options.closurePass = flags.process_closure_primitives;
    initOptionsFromFlags(options);
    return options;
```
<br>

## 2. Used chunks and locations - 1 chunk / 4 location
```java
src/com/google/javascript/jscomp/CommandLineRunner.java: 433-435
if (flags.process_closure_primitives) {
    options.closurePass = true;
}

src/com/google/javascript/jscomp/CommandLineRunner.java: 437
FAULT_OF_OMISSION
```
* Location 436 is not a blank location related to "FAULT_OF_OMISSION."
<br>

## 3. Correct combined patches per bug type
* T2F: 12, 19
<br><br>

## 4. Examples of correct patches
### 4.1. 12nd patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/CommandLineRunner.java: 433-438
-   if (flags.process_closure_primitives) {
-       options.closurePass = true;
-   }

+   options.closurePass = (flags.process_closure_primitives);
    initOptionsFromFlags(options);
    return options;
```
<br>

#### II. Fixed chunks and locations - 1 chunk / 4 locations
```java
src/com/google/javascript/jscomp/CommandLineRunner.java: 433-435
Location 433 was deleted.
Location 434 was deleted.
Location 435 was deleted.

src/com/google/javascript/jscomp/CommandLineRunner.java: 437
A location was inserted in front of Location 437.
```
<br>

### 4.2. 19th patch - T1F
#### I. Fixed Result
```java
src/com/google/javascript/jscomp/CommandLineRunner.java: 433-438
-   if (flags.process_closure_primitives) {
-       options.closurePass = true;
-   }

+   options.closurePass = flags.process_closure_primitives;
    initOptionsFromFlags(options);
    return options;
```

#### II. Fixed chunks and locations - 1 chunk / 4 locations
```java
src/com/google/javascript/jscomp/CommandLineRunner.java: 433-435
Location 433 was deleted.
Location 434 was deleted.
Location 435 was deleted.

src/com/google/javascript/jscomp/CommandLineRunner.java: 437
A location was inserted in front of Location 437.
```
<br><br>