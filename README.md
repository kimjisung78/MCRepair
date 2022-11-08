# MCRepair
* An Automated Program Repair (APR) technique that applied a buggy block, patch optimization, and CodeBERT to target complex multi-chunk bugs.
  * Buggy block: A novel method that binds buggy chunks into a multi-buggy chunk and preprocesses the chunk with its buggy contexts for patch space reduction and dependency problems.
  * Patch optimization: A novel strategy that effectively combines the generated candidate patches with patch space reduction.
  * CodeBERT: A BERT for source code datasets to address the lack of datasets and out-of-vocabulary problems. 
* Figures
  * [Figure 1:](./figures/Figure1.png) An overview of MCRepair.
    <img src="./figures/Figure1.png" width="100%"/>
  * [Figure 2:](./figures/Figure2.png) The details of Ingredient Extraction and Buggy Block Preprocessing about an example of the source code datasets.
  * [Figure 3:](./figures/Figure3.png) The details of Patch Optimization of the Candidate Patches.
  * [Figure 4:](./figures/Figure4.png) RQ1. Venn Diagram for Table 3.
<br><br>

## 1. Location-level criterion
* We did not consider null, blank, and comment locations that were not related to “FAULT_OF_OMISSION.”
    - “FAULT_OF_OMISSION” is a buggy location related to insertions.
    - A null location is a location that only includes “;” or does nothing (e.g., “;” and “for (int i = 0; i < 10; i++);”).
    - A block’s end is not a null location because the block designates a flow range.
* We checked whether each location was correct.
* We distinguished divided and overlapped locations.
<br><br>

## 2. Bug types
The difficulties are in the order of Type 3, Type 2, and Type 1. If an APR technique has Type 1, Type 2, and Type 3 in a module, we resulted in Type 3 based on the difficulties.

* Type 1: A single-chunk bug that uses or fixes a location
    - T1B: A Type 1 bug that uses a location for fixing
    - T1F: A Type 1 bug that fixes a location
* Type 2: A single-chunk bug that uses or fixes locations
    - T2B: A Type 2 bug that use locations for fixing
    - T2F: A Type 2 bug that fixes locations
*  Type 3: A multi-chunk bug that uses or fixes chunks
    - T3B: A Type 3 bug that uses chunks for fixing
    - T3F: A Type 3 bug that fixes chunks
<br><br>

## 3. Statstics of bugs (66/75)
```powershell
  |--- Total (66/75)
  |------ Chart (5/6)
  |--------- Plausible (1) : [C_24]
  |--------- Correct (5)   : [C_1, 8, 9, 11, 20]
  |------ Closure (21/21)
  |--------- Correct(21)   : [CL_2, 7, 10, 11, 13, 19, 38, 40, 46, 57, 62, 70, 86, 92, 101, 102, 107, 109, 115, 122, 125]
  |------ Lang (9/10)
  |--------- Plausible (1) : [L_55]
  |--------- Correct (9)   : [L_6, 10, 29, 34, 43, 51, 57, 59, 64]
  |------ Math (24/30)
  |--------- Plausible (6) : [M_33, 62, 73, 84, 95, 96]
  |--------- Correct (24)  : [M_2, 5, 8, 18, 22, 27, 30, 32, 34, 41, 46, 57, 58, 63, 70, 72, 75, 77, 79, 80, 82, 85, 98, 104]
  |------ Mockito (4/4) 
  |--------- Correct (4)   : [MC_1, 5, 22, 29]
  |------ Time (3/4)
  |--------- Plausible (1) : [T_18]
  |--------- Correct (3)   : [T_4, 17, 19]
```
<br><br>

## 4. Details of correctly repaired bugs (66)
* Chart (5)
  * [C_1](./markdowns/Chart_1.md), [C_8](./markdowns/Chart_8.md), [C_9](./markdowns/Chart_9.md)
  * [C_11](./markdowns/Chart_11.md)
  * [C_20](./markdowns/Chart_20.md)
* Closure (21)
  * [CL_2](./markdowns/Closure_2.md), [CL_7](./markdowns/Closure_7.md)
  * [CL_10](./markdowns/Closure_10.md), [CL_11](./markdowns/Closure_11.md), [CL_13](./markdowns/Closure_13.md), [CL_19](./markdowns/Closure_19.md)
  * [CL_38](./markdowns/Closure_38.md)
  * [CL_40](./markdowns/Closure_40.md), [CL_46](./markdowns/Closure_46.md)
  * [CL_57](./markdowns/Closure_57.md)
  * [CL_62](./markdowns/Closure_62.md)
  * [CL_70](./markdowns/Closure_70.md)
  * [CL_86](./markdowns/Closure_86.md)
  * [CL_92](./markdowns/Closure_92.md)
  * [CL_101](./markdowns/Closure_101.md), [CL_102](./markdowns/Closure_102.md), [CL_107](./markdowns/Closure_107.md), [CL_109](./markdowns/Closure_109.md)
  * [CL_115](./markdowns/Closure_115.md)
  * [CL_122](./markdowns/Closure_122.md), [CL_125](./markdowns/Closure_125.md)
* Lang (9)
  * [L_6](./markdowns/Lang_6.md)
  * [L_10](./markdowns/Lang_10.md)
  * [L_29](./markdowns/Lang_29.md)
  * [L_34](./markdowns/Lang_34.md)
  * [L_43](./markdowns/Lang_43.md)
  * [L_51](./markdowns/Lang_51.md), [L_57](./markdowns/Lang_57.md), [L_59](./markdowns/Lang_59.md)
  * [L_64](./markdowns/Lang_64.md)
* Math (24)
  * [M_2](./markdowns/Math_2.md), [M_5](./markdowns/Math_5.md), [M_8](./markdowns/Math_8.md)
  * [M_18](./markdowns/Math_18.md)
  * [M_22](./markdowns/Math_22.md), [M_27](./markdowns/Math_27.md)
  * [M_30](./markdowns/Math_30.md), [M_32](./markdowns/Math_32.md), [M_34](./markdowns/Math_34.md)
  * [M_41](./markdowns/Math_41.md), [M_46](./markdowns/Math_46.md)
  * [M_57](./markdowns/Math_57.md), [M_58](./markdowns/Math_58.md)
  * [M_63](./markdowns/Math_63.md)
  * [M_70](./markdowns/Math_70.md), [M_72](./markdowns/Math_72.md), [M_75](./markdowns/Math_75.md), [M_77](./markdowns/Math_77.md), [M_79](./markdowns/Math_79.md)
  * [M_80](./markdowns/Math_80.md), [M_82](./markdowns/Math_82.md), [M_85](./markdowns/Math_85.md)
  * [M_98](./markdowns/Math_98.md)
  * [M_104](./markdowns/Math_104.md)
* Mockito (4)
  * [MC_1](./markdowns/Mockito_1.md), [MC_5](./markdowns/Mockito_5.md)
  * [MC_22](./markdowns/Mockito_22.md), [MC_29](./markdowns/Mockito_29.md)
* Time (3)
  * [T_4](./markdowns/Time_4.md)
  * [T_17](./markdowns/Time_17.md), [T_19](./markdowns/Time_19.md)
<br><br>

## 5. Statstics of correctly repaired bugs (66)
### 5.1. Statstics of correctly repaired bugs (66)
```powershell
  |--- Total (66)
  |------ Chart (5)    : [C_1, 8, 9, 11, 20]
  |------ Closure (21) : [CL_2, 7, 10, 11, 13, 19, 38, 40, 46, 57, 62, 70, 86, 92, 101, 102, 107, 109, 115, 122, 125]
  |------ Lang (9)     : [L_6, 10, 29, 34, 43, 51, 57, 59, 64]
  |------ Math (24)    : [M_2, 5, 8, 18, 22, 27, 30, 32, 34, 41, 46, 57, 58, 63, 70, 72, 75, 77, 79, 80, 82, 85, 98, 104]
  |------ Mockito (4)  : [MC_1, 5, 22, 29]
  |------ Time (3)     : [T_4, 17, 19]
```
<br>

### 5.2. Statstics of correctly repaired bugs per bug type (66)
```powershell
  |--- Total (66)
  |------ Chart (5)
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
<br>

### 5.3. Statstics of correctly repaired bugs per chunk (66)
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
  |--------- Closure (5)   : [CL_2, 7, 11, 40, 115]
  |--------- Lang (3)      : [L_10, 34, 64]
  |--------- Math (7)      : [M_8, 22, 46, 72, 77, 79, 98]
  |--------- Time (1)      : [T_17]
  |------ 3 chunks (3)
  |--------- Closure (3)   : [CL_13, 46, 102]
  |------ 4 chunks (1)
  |--------- Math (1)      : [M_18]
```
<br>

### 5.4. Statstics of correctly repaired bugs per location (66)
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
  |--------- Closure (3)   : [CL_7, 19, 107]
  |--------- Lang (2)      : [L_34, 64]
  |--------- Math (6)      : [M_8, 22, 46, 72, 79, 98]
  |------ 3 locations (7)
  |--------- Closure (5)   : [CL_11, 13, 40, 86, 02]
  |--------- Lang (1)      : [L_51]
  |--------- Mockito (1)   : [MC_1]
  |------ 4 locations (3)
  |--------- Closure (2)   : [CL_2, 101]
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

