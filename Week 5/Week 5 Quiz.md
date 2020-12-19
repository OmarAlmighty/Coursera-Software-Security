# Week 5 quiz
##### 1. A static analysis

 - is a kind of real analysis for solving numeric equations
 - analyzes the fixed, or static portions of a program
 - is always better than testing
 ***- analyzes a program's code without running it***

##### 2. Which of the following are advantages of static analysis over testing?

 - A static analysis runs faster than testing
 - A static analysis is more precise than testing
 - ***A static analysis can analyze programs that are not necessarily executable on their own, e.g., libraries***
 - ***A static analysis can reason about all program paths, not just some of them***
 
 ##### 3. The halting problem is the problem of determining, for an arbitrary program and input, whether the program will finish running or continue to run forever. Which of the following statements about the halting problem are true?
 - You cannot build an automated analysis that proves that a particular
   program P terminates.
 - ***Many other program analysis problems can be converted to the halting
   problem.***
 - You cannot solve the halting problem with static analysis, but you
   can with symbolic execution.
 
 #####  Which of the following are not the advantages of static analysis over testing?
 - ***A static analysis is usually more scalable than testing***
 - ***A static analysis is more precise than testing***
 
 ##### 4. Suppose we have a static analysis that aims to find buffer overflows in C programs. If the analysis is sound, then which of the following is true about it?
 - ***It may have false alarms, but will not fail to report actual bugs***
 - It will not have any false alarms, but may fail to report actual bugs
 - It will report all actual bugs, and have no false alarms
 - It may miss bugs, and have false alarms
 
 ##### 5. A tainted flow is
 - ***A flow from an untrusted source to both trusted and untrusted sinks***
 - ***A flow from an untrusted source to a trusted sink***
 - A flow from a trusted source to an untrusted sink
 - A flow from a trusted source to both trusted and untrusted sinks
 
 ##### 6. (4 points) Consider the program below, using the qualified types annotations for tainted flows given in the lecture (shown in comments). In particular, notice that the variable fmt and the argument to printf are untainted, while the result of fgets is tainted. Suppose we analyze this with a tainted flow analysis. This program has no bugs, but which kinds of analysis report a false alarm? XXXX!
```sh
/* int printf(untainted char *fstr, ...); */

/* tainted char *fgets(...); */

char *chomp(char *s) {

int i, len = strlen(s);

for (i = 0; i<len; i++)

if (s[i] == '\n') {

s[i] = '\0';

break;

}

return s;

}

void foo(FILE *networkFP, untainted char *fmt) {

char buf[100];

char *str = fgets(buf, sizeof(buf), networkFP);

char *str1 = chomp(str);

char *fmt1 = chomp(fmt);

printf(fmt1,str1);

}
```

 - flow-sensitive, context-sensitive
 - path-sensitive, context-sensitive
 - flow-sensitive, context-Insensitive
 - path-sensitive, context-INsensitive
 - flow-INsensitive, context-Insensitive

##### 7. (4 points) Consider the following code, where the referenced chomp function is the same as in the previous question. Suppose we analyze this with a tainted flow analysis. Once again, this program has no bugs, but which kinds of analysis report a false alarm? XXXXX!
```sh
void bar(FILE *networkFP, char *fmt, int testing) {

char buf[100];

char *str = fgets(buf, sizeof(buf), networkFP);

char *str1 = chomp(str);

if (testing)

str1 = "test format";

printf(fmt,str1);

if (testing)

printf(str1);

}
```

 - ***flow-sensitive, context-sensitive***
 - ***path-sensitive, context-sensitive***
 - path-sensitive, context-INsensitive
 - ***flow-sensitive, context-INsensitive***
 - flow-INsensitive, context-INsensitive
 
 ##### 8. Which of the following are true of implicit flows?
 - ***One can occur when assigning an untainted value to an untainted
   variable, but conditioned on a tainted value***
 - ***Implicit flows are rarely detected by tainted flow analyses, because
   detecting them can increase false alarms***
 - They only arise in object-oriented languages with dynamic dispatch,
   since the choice of method to call is implicit
 
 ##### 9. What is a key advantage of symbolic execution over static analysis?
 - Symbolic executors consider all possible program runs, while static
   analyses don't
 - ***As a generalized form of testing, when a symbolic executor finds a
   bug, we are sure it is not a false alarm***
 - Symbolic executors can consider partial programs (e.g., libraries)
   while static analyzers cannot
 - Symbolic executors are both sound and complete, while static
   analyzers can only be one or the other
 
 ##### 10. Symbolic execution, viewed as a kind of static analysis, has which of the following "sensitivities?"
 - Flow-sensitivity
 - Context-sensitivity
 - Path-sensitivity
 - ***All of the above***
 
 ##### 11. Why is concolic execution problematic for non-terminating programs?
 - ***Its search strategy is to choose new test cases based on constraints
   generated by terminating runs***
 - Concolic execution takes a breadth-first approach, but
   non-terminating programs are better suited to a depth-first approach
 - Non-terminating programs will consume too many resources
 - Non-terminating programs require user interaction, which concolic
   execution does not handle
 
 ##### 12. Suppose that x and y in the following program are symbolic. When the symbolic executor reaches the line that prints "everywhere" what will the path condition be?
```sh
/* assume x and y are both symbolic */

void foo(int x, int y) {

if (x > 5) {

if (y > 7) {

printf("here\n");

} else {

if (x < 20)

printf("everywhere\n");

else

printf("nowhere\n");

}

}

}
```

 - �(y > 7) ? x < 20
 - x > 5 ?  �(y > 7) ?  �(x < 20)
 - ***x > 5 ?  �(y > 7) ? x < 20***
 - x > 5 ? y > 7 ? x < 20
 
 ##### 13. Suppose that x in the following program is symbolic. When the symbolic executor reaches the line that prints "here" what will the path condition be?
```sh
void bar(int x) {

int z;

if (x > 5)

z = 5;

else

z = 1;

if (z > 3)

printf("here\n");

}
```

 - x > 5 ? z > 3
 - ***x > 5***
 - �(x > 5) ? z > 3
 - z > 3
 
 ##### 14. Which of the following are heuristics that symbolic executors use to cover more of the search space?
 - Switch between concolic and non-concolic execution
 - ***Choose between two paths based on a notion of priority***
 - ***Choose between two paths based on whether one reaches program statements not previously executed***
 - ***Randomly restart the search from the main function***
