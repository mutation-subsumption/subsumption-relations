---
layout: default
title: "lhs &= rhs"
permalink: /relations/and-assigment/
---

## Target: ``lhs &= rhs``

## Snippet


```java
public int and(int lexp, int rexp) {
    lexp &= rexp;
    return lexp;
}
```


### DMSG

![image](images/dmsg_and-assigment.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 4                   | 2                  |50.00%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ASRS     | 2        | 0         | 0        | **2**  |
| ODL      | 1        | 0         | 0        | **1**  |
| SDL      | 1        | 0         | 0        | **1**  |
|**Total** | **4**    | **0**     | **0**    | **4**  |
