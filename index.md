# Optimizing Mutation Testing by Discovering Dynamic Mutant Subsumption Relations

Abstract—Mutation analysis is a popular but costly approach to assess the quality of test suites. One recent promising direction on reducing costs of mutation analysis is to identify redundant mutations, i.e., mutations that are subsumed by some other mutations. Previous works found out redundant mutants manually through the truth table. Although the idea is promising, it can only be applied for logical and relational operators. In this paper, we propose an approach to discover redundancy in mutations through dynamic subsumption relations among mutants. Past work has demonstrated that finding out the true subsumption relation among mutants in large blocks of code (like a class or a function) is difficult (in some cases computationally infeasible), mainly because of the context-information that needs to be taken into account. This way, we reduced the scope and focused on subsumption relations among mutations of an expression or statement, named here as “mutation target.” By focusing on targets and relying on automatic test generation tools, we defined subsumption relations for dozens of mutation targets in which the MuJava tool can apply mutations. We then implemented these relations in a tool, named MuJava-M, that generates a reduced set of mutants for each target, avoiding redundant mutants. We evaluated MuJava and MuJava-M using classes of industrial-scale projects. Our results indicate that MuJava-M generates less mutants (on average 53.33% less) with 100% of effectiveness in 19 out of 32 targets and more than 90% in 29 out of 32 mutation targets. MuJava-M also reduced the time to execute the test suites against the mutants in 52.53% on average, considering the full mutation analysis process.

# Tools 

### Hunor 
We created a tool called Hunor to automate various steps of the study. We also developed hunor-maven-plugin to facilitate the execution of MuJava, MuJava-M, and mutation analysis in maven projects. To replicate the study or run the tools on other subjects, we provide a Docker image that contains all the tools and settings needed to run Hunor a maven project. The image is available on Docker Hub at https://hub.docker.com/r/mutationsubsumption/hunor.

In each step of the study, we show the docker-compose configuration needed to replicate the experiment.


# Discover Dynamic Subsumption Relations



The docker-compose file shown below runs Hunor with the necessary parameters to generate the DMSG that represents the dynamic subsuming relationship on all project targets.
 
With Docker and Docker Compose installed on your machine, follow these steps:

1) Create or use an existing maven project.
2) Add the *docker-compose.yml* file to the project root, along with the [*config.json*](https://raw.githubusercontent.com/mutation-subsumption/subsumption-relations/master/config-discover.json) configuration file.
3) Run docker-composer with the command:

*docker-compose.yml*
```yml
version: '3'
services:
  hunor:
    image: mutationsubsumption/hunor:0.9.8
    working_dir: /opt/src
    command: [
      'hunor-pgen',
      '-j', '/usr/local/openjdk-8',
      '-m', '/usr/share/maven',
      '-c', 'config.json',
      '--coverage-threshold', '0',
      '--mutation-tool', 'mujava',
      '--mutants', 'mutants',
      '--disable-minimal-testsuite',
      '--enable-new-mutations',
      '--suites-evosuite', '5',
      '--suites-randoop', '5'
    ]
    volumes:
      - .:/opt/src
```



### Binary expressions with arithmethic operators

[``lexp + rexp``](relations/lexp-plus-rexp/) 
[``lexp - rexp``](relations/lexp-minus-rexp/) 
[``lexp * rexp``](relations/lexp-times-rexp/) 
[``lexp / rexp``](relations/lexp-div-rexp/) 
[``lexp % rexp``](relations/lexp-mod-rexp/) 

### Binary expressions with logical operators

[``lexp && rexp``](relations/lexp-and-rexp/) 
[``lexp || rexp``](relations/lexp-or-rexp/) 
[``lexp ^ rexp``](relations/lexp-xor-rexp/) 

### Binary expressions with relational operators

[``lexp == rexp``](relations/lexp-equal-rexp/) 
[``lexp != rexp``](relations/lexp-notequal-rexp/) 
[``lexp > rexp``](relations/lexp-gt-rexp/) 
[``lexp >= rexp``](relations/lexp-gte-rexp/) 
[``lexp < rexp``](relations/lexp-lt-rexp/) 
[``lexp <= rexp``](relations/lexp-lte-rexp/) 

### Binary expressions with bitwise operators

[``lexp & rexp``](relations/lexp-bit-and-rexp/) 
[``lexp | rexp``](relations/lexp-bit-or-rexp/) 
[``lexp ^ rexp``](relations/lexp-bit-xor-rexp/) 

### Unary Expression

[``exp``](relations/exp/) 
[``+exp``](relations/plus-exp/) 
[``-exp``](relations/minus-exp/) 
[``++exp``](relations/preinc-exp/) 
[``exp++``](relations/posinc-exp/) 
[``--exp``](relations/predec-exp/) 
[``exp--``](relations/posdec-exp/) 
[``!exp``](relations/not-exp/) 
[``~exp``](relations/bit-not-exp/) 

### Arithmetic Compound Assigment

[``lhs += rhs``](relations/plus-assigment/) 
[``lhs -= rh``](relations/minus-assigment/) 
[``lhs *= rh``](relations/times-assigment/) 
[``lhs /= rh``](relations/div-assigment/) 
[``lhs %= rh``](relations/mod-assigment/) 

### Bit Shift Compound Assigment

[``lhs <<= rh``](relations/leftbit-assigment/) 
[``lhs >>= rh``](relations/rightbit-assigment/) 
[``lhs >>>= rh``](relations/rightunsignedbit-assigment/) 

### Logical Compound Assigment

[``lhs &= rh``](relations/and-assigment/) 
[``lhs |= rh``](relations/or-assigment/) 
[``lhs ^= rh``](relations/xor-assigment/) 


## Subjects

| Project        | Version          | CLOC       |
| :---           |             ---: |       ---: |
| joda-time      |           2.10.1 |     28,790 |
| commons-math   |            3.6.1 |    100,364 |
| commons-lang   |              3.6 |     27,267 |
| h2             |          1.4.199 |    134,234 |
| javassist      |             3.20 |     35,249 |


### RQ 1: _How many mutants are likely-subsumed?_

1) Download the source-code of subjects analyzed.
2) Add the *docker-compose.yml* file to the project root, use the config.json files corresponding to each subject.
3) Run docker-composer with the command ``docker-compose up``


*docker-compose.yml*
```yml
version: '3'
services:
  hunor:
    image: hunor:0.9.8
    working_dir: /opt/src
    command: [
      'hunor-eval',
      '-j', '/usr/local/openjdk-8',
      '-m', '/usr/share/maven',
      '-c', 'config.json',
      '--coverage-threshold', '0',
      '--mutation-tool', 'mujava',
      '--mutants', 'mutants',
      '--disable-minimal-testsuite',
      '--enable-new-mutations'
    ]
    volumes:
      - .:/opt/src
```

**joda-time (2.10.1)**

```sh
git clone https://github.com/JodaOrg/joda-time -b v2.10.1
```

*config.json*
```json
{
    "project": "joda-time",
    "source": [
        "."
    ],
    "java_src": ["src", "main", "java"]
}
```

**commons-math (3.6.1)**

```sh
git clone https://github.com/apache/commons-math -b 3.6.1-release
```

*config.json*
```json
{
    "project": "commons-math",
    "source": [
        "."
    ],
    "java_src": ["src", "main", "java"]
}

```

**commons-lang (3.6)**

```sh
git clone https://github.com/apache/commons-lang -b LANG_3_6
```

*config.json*
```json
{
    "project": "commons-lang",
    "source": [
        "."
    ],
    "java_src": ["src", "main", "java"]
}
```
**h2 (1.4.199)**
```sh
git clone https://github.com/h2database/h2database -b 1.4.199
```

*config.json*
```json
{
    "project": "h2",
    "source": [
        "."
    ],
    "java_src": ["src", "main"]
}
```

**javassist (3.20)**

```sh
git clone https://github.com/jboss-javassist/javassist -b 3.20
```

*config.json*
```json
{
    "project": "javassist",
    "source": [
        "."
    ],
    "java_src": ["src", "main"]
}
```


[Reduction and Effectiviness.csv](https://raw.githubusercontent.com/mutation-subsumption/subsumption-relations/master/Reduction%20and%20Effectiveness.csv)

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

1) Download the source-code of subjects analyzed.
2) Add the *docker-compose.yml* file to the project root, use the config.json files corresponding to each subject.
3) Run docker-composer with the command ``docker-compose up``

*docker-compose.yml*
```yml
version: '3'
services:
  hunor:
    image: hunor:0.9.13
    working_dir: /opt/src
    command: [
      'hunor-time',
      '-j', '/usr/local/openjdk-8',
      '-m', '/usr/share/maven',
      '-c', 'config.json',
      '--coverage-threshold', '0',
      '--mutation-tool', 'mujava',
      '--mutants', 'mutants',
      '--disable-minimal-testsuite',
      '--enable-new-mutations'
    ]
    volumes:
      - .:/opt/src
```

**joda-time (2.10.1)**

```sh
git clone https://github.com/JodaOrg/joda-time -b v2.10.1
```

*config.json*
```json
{
    "project": "joda-time",
    "source": [
        "."
    ],
    "java_src": ["src", "main", "java"],
    "include": [
        "org/joda/time/field/FieldUtils.java",
        "org/joda/time/MutableDateTime.java",
        "org/joda/time/chrono/ISOYearOfEraDateTimeField.java",
        "org/joda/time/MutableInterval.java",
        "org/joda/time/field/UnsupportedDateTimeField.java",
        "org/joda/time/chrono/GJMonthOfYearDateTimeField.java"
    ]
}
```

**commons-math (3.6.1)**

```sh
git clone https://github.com/apache/commons-math -b 3.6.1-release
```

*config.json*
```json
{
    "project": "commons-math",
    "source": [
        "."
    ],
    "java_src": ["src", "main", "java"],
    "include": [
       "org/apache/commons/math3/optimization/univariate/BrentOptimizer.java",
       "org/apache/commons/math3/optim/nonlinear/scalar/LeastSquaresConverter.java",
       "org/apache/commons/math3/optim/SimpleValueChecker.java",
       "org/apache/commons/math3/linear/DefaultIterativeLinearSolverEvent.java",
       "org/apache/commons/math3/analysis/FunctionUtils.java"
    ]

}

```

**commons-lang (3.6)**

```sh
git clone https://github.com/apache/commons-lang -b LANG_3_6
```

*config.json*
```json
{
    "project": "commons-lang",
    "source": [
        "."
    ],
    "java_src": ["src", "main", "java"],
    "include": [
        "org/apache/commons/lang3/math/IEEE754rUtils.java",
        "org/apache/commons/lang3/mutable/MutableInt.java",
        "org/apache/commons/lang3/ClassPathUtils.java",
        "org/apache/commons/lang3/mutable/MutableObject.java",
        "org/apache/commons/lang3/concurrent/ConstantInitializer.java"
    ]
}
```

**javassist (3.20)**

```sh
git clone https://github.com/jboss-javassist/javassist -b 3.20
```

*config.json*
```json
{
    "project": "javassist",
    "source": [
        "."
    ],
    "java_src": ["src", "main"],
    "include": [
	"javassist/bytecode/stackmap/MapMaker.java",
	"javassist/bytecode/annotation/TypeAnnotationsWriter.java",
	"javassist/expr/Handler.java",
	"javassist/bytecode/analysis/Subroutine.java",
	"javassist/compiler/ast/Keyword.java"
    ]
}
```



