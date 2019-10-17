---
layout: default
title: "--exp"
permalink: /relations/predec-exp/
---

## Target: ``--exp``

## Snippet


```java
public int decrementPrefix(int exp) {
    return --exp;
}
```


### DMSG

![image](images/dmsg_predec-exp.png)

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
| AORS     | 1        | 0         | 0        | **1**  |
| AODS     | 1        | 0         | 0        | **1**  |
| LOI      | 1        | -1        | 0        | **0**  |
|**Total** | **5**    | **-2**    | **0**    | **3**  |
