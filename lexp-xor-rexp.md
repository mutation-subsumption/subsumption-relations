---
layout: default
title: "lexp ^ rexp"
permalink: /relations/lexp-xor-rexp/
---

# Target: ``lexp ^ rexp``

## Snippet


```java
public boolean xor(boolean lexp, boolean rexp) {
    return lexp ^ rexp;
}
```


### DMSG

![image](images/dmsg_lexp-xor-rexp.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 10                  | 2                  |80.00%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ODL      | 2        | 0         | 0        | **2**  |
| VDL/CDL  | 2        | 0         | 0        | **2**  |
| COR      | 6        | 0         | -1       | **5**  |
| COI      | 1        | 0         | 0        | **1**  |
|**Total** | **11**   | **0**     | **-1**   | **10** |
