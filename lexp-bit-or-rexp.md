---
layout: default
title: "lexp | rexp"
permalink: /relations/lexp-bit-or-rexp/
---
# Target: ``lexp | rexp``

## Snippet


```java
public int or(int lexp, int rexp) {
    return lexp | rexp;
}
```


### DMSG

![image](images/dmsg_lexp-bor-rexp.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 6                   | 3                  |50.00%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ODL      | 2        | 0         | 0        | **2**  |
| VDL/CDL  | 2        | 0         | 0        | **2**  |
| LOR      | 2        | 0         | 0        | **2**  |
|**Total** | **6**    | **0**     | **0**    | **6**  |
