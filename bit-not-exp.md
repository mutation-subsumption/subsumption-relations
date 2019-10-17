---
layout: default
title: "~exp"
permalink: /relations/bit-not-exp/
---

## Target: ``~exp``

## Snippet


```java
public int complement(int exp) {
    return ~exp;
}
```


### DMSG

![image](images/dmsg_bnot-exp.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 3                   | 1                  |66.67%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ODL      | 1        | 0         | 0        | **1**  |
| VDL/CDL  | 1        | -1        | 0        | **0**  |
| LOD      | 1        | 0         | 0        | **1**  |
| LOI      | 1        | 0         | 0        | **1**  |
|**Total** | **4**    | **-1**    | **0**    | **3**  |
