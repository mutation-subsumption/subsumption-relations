---
layout: default
title: "exp++"
permalink: /relations/posinc-exp/
---

## Target: ``exp++``

## Snippet


```java
public int incrementPostfix(int exp) {
    return exp++;
}
```


### DMSG

![image](images/dmsg_posinc-exp.png)

## Sufficient Mutants


|Total of Mutants¹    | Sufficient Mutants |Reduction |
|                ---: |               ---: |     ---: |  
| 1                   | 1                  |00.00%    |

¹Excluding stillborn and stubborn mutants.

## Mutants



| Operator | #Mutants | Stillborn | Stubborn | Total  |
| :---     |     ---: |      ---: |     ---: |   ---: |
| ODL      | 1        | 0         | -1       | **0**  |
| VDL/CDL  | 1        | -1        | 0        | **0**  |
| AORS     | 1        | 0         | -1       | **0**  |
| AODS     | 1        | 0         | -1       | **0**  |
| LOI      | 1        | 0         | 0        | **1**  |
|**Total** | **5**    | **-1**    | **3**    | **1**  |

