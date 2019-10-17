---
layout: default
title: "lexp ^ rexp"
permalink: /relations/lexp-bit-xor-rexp/
---

# Target: ``lexp  rexp``

## Snippet


```java
public int xor(int lexp, int rexp) {
    return lexp ^ rexp;
}
```


### DMSG

![image](images/dmsg_lexp-bxor-rexp.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 6                   | 1                  |83.34%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ODL      | 2        | 0         | 0        | **2**  |
| VDL/CDL  | 2        | 0         | 0        | **2**  |
| LOR      | 2        | 0         | 0        | **2**  |
|**Total** | **6**    | **0**     | **0**    | **6**  |
