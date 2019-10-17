---
layout: default
title: "lhs ^= rhs"
permalink: /relations/xor-assigment/
---

---

## Target: ``lhs ^= rhs``

## Snippet


```java
public int xor(int lexp, int rexp) {
    lexp ^= rexp;
    return lexp;
}
```


### DMSG

![image](images/dmsg_xor-assigment.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 4                   | 1                  |75.00%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ASRS     | 2        | 0         | 0        | **2**  |
| ODL      | 1        | 0         | 0        | **1**  |
| SDL      | 1        | 0         | 0        | **1**  |
|**Total** | **4**    | **0**     | **0**    | **4**  |
