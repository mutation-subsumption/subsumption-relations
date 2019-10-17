---
layout: default
title: "lhs <<= rhs"
permalink: /relations/leftbit-assigment/
---

## Target: ``lhs <<= rhs``

## Snippet


```java
public int leftShift(int lexp, int rexp) {
    lexp <<= rexp;
    return lexp;
}
```


### DMSG

![image](images/dmsg_leftbit-assigment.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 3                   | 1                  | 66.67%   |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ASRS     | 1        | 0         | 0        | **1**  |
| ODL      | 1        | 0         | 0        | **1**  |
| SDL      | 1        | 0         | 0        | **1**  |
|**Total** | **3**    | **0**     | **0**    | **3**  |
