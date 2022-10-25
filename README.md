# MCRepair
* An Automated Program Repair (APR) that applied buggy block, patch optimization, and CodeBERT to target multi-chunk bugs.
<br><br>

## 1. Location-level criterion
* We did not consider null, blank, and comment locations that were not related to “FAULT_OF_OMISSION”
    - “FAULT_OF_OMISSION” is a buggy location related to insertions.
    - A null location is a location that only includes “;” or does nothing. (e.g., “;” and “for (int i = 0; i < 10; i++);”)
    - A block’s end is not a null location because the block designates a flow range.
* We checked whether each location was correct.
* We distinguished divided and overlapped locations.
<br><br>

## 2. Bug types
The difficulties are in order of Type 3, Type 2, and Type 1. If an APR technique has Type 1, Type 2, and Type 3 in a module, we resulted the module in Type 3 based on the difficulties.

* Type 1: Single-chunk bugs that use single-location for fixing or fix single-location
    - T1B: Type 1 bugs that use single-location for fixing
    - T1F: Type 1 bugs that fix single-location
* Type 2: Single-chunk bugs that use multi-location for fixing or fix multi-location
    - T2B: Type 2 bugs that use multi-location for fixing
    - T2F: Type 2 bugs that fix multi-location
*  Type 3: Multi-chunk bugs that use multi-chunk for fixing or fix multi-chunk
    - T3B: Type 3 bugs that use multi-chunk for fixing
    - T3F: Type 3 bugs that fix multi-chunk
<br><br>

## 3. Statstics of bugs (66/75)
```powershell
  |--- Total (66/75)
  |------ Chart (4/5)
  |--------- Plausible (1) : [C_24]
  |--------- Correct (4)   : [C_1, 8, 9, 11, 20]
  |------ Closure (21/21)
  |--------- Correct(21)   : [CL_2, 7, 10, 11, 13, 19, 38, 40, 46, 57, 62, 70, 86, 92, 101, 102, 107, 109, 115, 122, 125]
  |------ Lang (9/10)
  |--------- Plausible (1) : [L_55]
  |--------- Correct (9)   : [L_6, 10, 29, 34, 43, 51, 57, 59, 64]
  |------ Math (24/30)
  |--------- Plausible (6) : [M_33, 62, 73, 84, 95, 96]
  |--------- Correct (24)  : [M_2, 5, 8, 18, 22, 28, 30, 32, 34, 41, 46, 58, 58, 63, 70, 72, 75, 77, 79, 80, 82, 85, 98, 104]
  |------ Mockito (4/4) 
  |--------- Correct (4)   : [MC_1, 5, 22, 29]
  |------ Time (3/4)
  |--------- Plausible (1) : [T_18]
  |--------- Correct (3)   : [T_4, 17, 19]
```
<br><br>

## 4. Statstics of correctly repaired bugs (66)
### 4.1. Statstics of correctly repaired bugs (66)
```powershell
  |--- Total (66)
  |------ Chart (4)    : [C_1, 8, 9, 11, 20]
  |------ Closure (21) : [CL_2, 7, 10, 11, 13, 19, 38, 40, 46, 57, 62, 70, 86, 92, 101, 102, 107, 109, 115, 122, 125]
  |------ Lang (9)     : [L_6, 10, 29, 34, 43, 51, 57, 59, 64]
  |------ Math (24)    : [M_2, 5, 8, 18, 22, 28, 30, 32, 34, 41, 46, 58, 58, 63, 70, 72, 75, 77, 79, 80, 82, 85, 98, 104]
  |------ Mockito (4)  : [MC_1, 5, 22, 29]
  |------ Time (3)     : [T_4, 17, 19]
```
<br><br>

### 4.2. Statstics of correctly repaired bugs per bug type (66)
```powershell
  |--- Total (66)
  |------ Chart (4)
  |--------- Type 1 (4)    : [C_8, 9, 11, 20]
  |--------- Type 3 (1)    : [C_1]
  |------ Closure (21)
  |--------- Type 1 (9)    : [CL_10, 38, 57, 62, 70, 92, 109, 122, 125]
  |--------- Type 2 (4)    : [CL_19, 86, 101, 107]
  |--------- Type 3 (8)    : [CL_2, 7, 11, 13, 40, 46, 102, 115]
  |------ Lang (9)
  |--------- Type 1 (5)    : [L_6, 29, 43, 57, 59]
  |--------- Type 2 (1)    : [L_51]
  |--------- Type 3 (3)    : [L_10, 34, 64]
  |------ Math (24)
  |--------- Type 1 (15)   : [M_2, 5, 27, 30, 32, 34, 41, 57, 58, 70, 75, 80, 82, 85, 104]
  |--------- Type 2 (1)    : [M_63]
  |--------- Type 3 (8)    : [M_8, 18, 22, 46, 72, 77, 79, 98]
  |------ Mockito (4)
  |--------- Type 1 (3)    : [MC_5, 22, 29]
  |--------- Type 2 (1)    : [MC_1]
  |------ Time (3)
  |--------- Type 1 (2)    : [T_4, 19]
  |--------- Type 3 (1)    : [T_17]
```
<br><br>

### 4.3. Statstics of correctly repaired bugs per chunk (66)
```powershell
  |--- Total (66)
  |------ 1 chunk (45)
  |--------- Chart (4)     : [C_8, 9, 11, 20]
  |--------- Closure (13)  : [CL_10, 19, 38, 57, 62, 70, 86, 92, 101, 107, 109, 122, 125]
  |--------- Lang (6)      : [L_6, 29, 43, 51, 57, 59]
  |--------- Math (16)     : [M_2, 5, 27, 30, 32, 34, 41, 57, 58, 63, 70, 75, 80, 82, 85, 104]
  |--------- Mockito (4)   : [MC_1, 5, 22, 29]
  |--------- Time (2)      : [T_7, 19]
  |------ 2 chunks (17)
  |--------- Chart (1)     : [C_1]
  |--------- Closure (6)   : [CL_2, 7, 11, 40, 115]
  |--------- Lang (3)      : [L_10, 34, 64]
  |--------- Math (7)      : [M_8, 22, 46, 72, 77, 79, 98]
  |--------- Time (1)      : [T_17]
  |------ 3 chunks (3)
  |--------- Closure (3)   : [CL_13, 46, 102]
  |------ 4 chunks (1)
  |--------- Math (1)      : [M_18]
```
<br><br>

### 4.4. Statstics of correctly repaired bugs per location (66)
```powershell
  |--- Total (66)
  |------ 1 location (38)
  |--------- Chart (4)     : [C_8, 9, 11, 20]
  |--------- Closure (9)   : [CL_10, 38, 57, 62, 70, 92, 109, 122, 125]
  |--------- Lang (5)      : [L_6, 29, 43, 57, 59]
  |--------- Math (15)     : [M_2, 5, 27, 30, 32, 34, 41, 57, 58, 70, 75, 80, 82, 85, 104]
  |--------- Mockito (3)   : [MC_5, 22, 29]
  |--------- Time (2)      : [T_7, 19]
  |------ 2 locations (12)
  |--------- Chart (1)     : [C_1]
  |--------- Closure (2)   : [CL_7, 19]
  |--------- Lang (2)      : [L_34, 64]
  |--------- Math (6)      : [M_8, 22, 46, 72, 79, 98]
  |--------- Mockito (1)   : [MC_1]
  |------ 3 locations (6)
  |--------- Closure (5)   : [CL_11, 13, 86, 102, 107]
  |--------- Lang (1)      : [L_51]
  |------ 4 locations (4)
  |--------- Closure (3)   : [CL_2, 40, 101]
  |--------- Math (1)      : [M_18]
  |------ 5 locations (2)
  |--------- Math (1)      : [M_63]
  |--------- Time (1)      : [T_17]
  |------ 9 locations (1)
  |--------- Lang (1)      : [L_10]
  |------ 10 locations
  |--------- Math (1)      : [M_77]
  |------ 11 locations
  |--------- Closure (1)   : [CL_115]
  |------ 13 locations
  |--------- Closure (1)   : [CL_46]
```
<br><br>