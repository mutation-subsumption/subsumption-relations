# Optimizing Mutation Testing by Discovering Dynamic Mutant Subsumption Relations

Abstract—Mutation analysis is a popular but costly approach to assess the quality of test suites. One recent promising direction on reducing costs of mutation analysis is to identify redundant mutations, i.e., mutations that are subsumed by some other mutations. Previous works found out redundant mutants manually through the truth table. Although the idea is promising, it can only be applied for logical and relational operators. In this paper, we propose an approach to discover redundancy in mutations through dynamic subsumption relations among mutants. Past work has demonstrated that finding out the true subsumption relation among mutants in large blocks of code (like a class or a function) is difficult (in some cases computationally infeasible), mainly because of the context-information that needs to be taken into account. This way, we reduced the scope and focused on subsumption relations among mutations of an expression or statement, named here as “mutation target.” By focusing on targets and relying on automatic test generation tools, we defined subsumption relations for dozens of mutation targets in which the MuJava tool can apply mutations. We then implemented these relations in a tool, named MuJava-M, that generates a reduced set of mutants for each target, avoiding redundant mutants. We evaluated MuJava and MuJava-M using classes of industrial-scale projects. Our results indicate that MuJava-M generates less mutants (on average 53.33% less) with 100% of effectiveness in 19 out of 32 targets and more than 90% in 29 out of 32 mutation targets. MuJava-M also reduced the time to execute the test suites against the mutants in 52.53% on average, considering the full mutation analysis process.

## Subjects

| Project        | Version          | CLOC       |
| :---           |             ---: |       ---: |
| joda-time      |           2.10.1 |     28,790 |
| commons-math   |            3.6.1 |    100,364 |
| commons-lang   |              3.6 |     27,267 |
| h2             |          1.4.199 |    134,234 |
| javassist      |             3.20 |     35,249 |


### RQ 1: _How many mutants are likely-subsumed?_



### RQ 2: _How many mutants are incorrectly discarded from the minimal set?_

*Example 1*:

```java
public void append(int inner, int outer, int name, int flags) {
    byte[] data = get();
    int len = data.length;
    byte[] newData = new byte[len + 8];
    for (int i = 2; i < len; ++i)
        newData[i] = data[i];

    int n = ByteArray.readU16bit(data, 0);
    ByteArray.write16bit(n + 1, newData, 0);

    ByteArray.write16bit(inner, newData, len);
    ByteArray.write16bit(outer, newData, len + 2);
    ByteArray.write16bit(name, newData, len + 4);
    ByteArray.write16bit(flags, newData, len + 6);

    set(newData);
}
```

In the append method, we have the expression ``len + 8`` (Line 4). This expression is used to define the length of an array in a local variable. The minimal mutation set defined for this target would be: ``ODL lexp`` (``len + 8 7→ len``), ``ODL rexp`` (``len + 8 7→ 8``), and ``AORB %`` (``len + 8 7→ len % 8``). However, the minimal test set did not kill the ``AORB *`` (``len + 8 7→ len * 8``) mutation. Initially, we thought that the mutant resulting from the ``AORB *`` mutation was equivalent, because it simply increases the array storage space and, in principle, would not change the behavior of the program. However, in Line 8 the newdata reference is passed as a parameter to a parent class method that uses newdata to change a byte array field.

_Example 2_:

```java
public static boolean xor(final boolean... array) {
    if (array == null) {
        throw new IllegalArgumentException("The Array must not be null");
    }
    if (array.length == 0) {
        throw new IllegalArgumentException("Array is empty");
    }

    boolean result = false;
    for (final boolean element : array) {
        result ^= element;
    }

    return result;
}
```

At Line 11 of the xor method there is the following statement: ``result ^= element``. This statement applies an exclusive disjunction logic operation among all elements of the array. The minimal mutation set for this target is made up of just one mutation: ``ASRS |=`` (``result ^= element 7→ result |= element``). However, the minimal test set did not kill the ``ASRS &=`` (``result ^= element 7→ result &= element``) mutation.

[Lindström and Márki](https://onlinelibrary.wiley.com/doi/full/10.1002/stvr.1667) suggest that the subsumption relations cannot hold when the mutated statements are re-executed (in the context of strong mutation). If the mutated instruction is executed more than once by any test execution, we cannot determine the future state of the program. Since our subsumption relations were obtained from a program where the final state is known, they are not sufficient to represent the mutation within a repeating context.

### RQ 3: _What are the time savings of eliminating likely-subsumed mutants?_
