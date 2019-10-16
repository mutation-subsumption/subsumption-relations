---
layout: default
title: "lexp > rexp"
permalink: /relations/lexp-gt-rexp/
---

# Target: ``lexp + rexp``

## Snippet


```java
public int sum(int lexp, int rexp) {
    return lexp + rexp;
}
```


### DMSG

![image](images/dmsg_lexp-plus_rexp.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 8                   | 3                  |62.50%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ODL      | 2        | 0         | 0        | **2**  |
| VDL/CDL  | 2        | 0         | 0        | **2**  |
| AORB     | 4        | 0         | 0        | **4**  |
|**Total** | **8**    | **0**     | **0**    | **8**  |
