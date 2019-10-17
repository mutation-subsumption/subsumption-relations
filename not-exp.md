---
layout: default
title: "!exp"
permalink: /relations/not-exp/
---

## Target: ``!exp``

## Snippet


```java
public boolean complement(boolean exp) {
    return !exp;
}
```


### DMSG

![image](images/dmsg_not-exp.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 2                   | 1                  |50.00%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ODL      | 1        | 0         | 0        | **1**  |
| VDL/CDL  | 1        | -1        | 0        | **0**  |
| COD      | 1        | 0         | 0        | **1**  |
|**Total** | **3**    | **-1**    | **0**    | **2**  |
