# Project 3 Quiz
##### 1. Does fuzz.py identify a crash in wisdom-alt? In how many iterations?

Identifies a crash, 103 iterations

Identifies a crash, 44 iterations

Does not identify a crash

***Identifies a crash, one iteration***

##### 2. Does fuzz.py identify a crash in wisdom-alt2? In how many iterations?

***Does not identify a crash***

Identifies a crash, 1 iteration

Identifies a crash, 133 iterations

Identifies a crash, 800 iterations

##### 3. Name one symbolic variable that was set in the path condition identified by KLEE that crashes wisdom-alt2.

***buf***

##### 4. Name another symbolic variable set in the path condition identified by KLEE that crashes wisdom-alt2.

***r***

##### 5. What was the data content of the buf object?

***�\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00�***

�\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\xFF\x00\x00\x00\x00\x00\x00\x00\x00\xAA�

�\x00\x00\x00\xFF\x00\x00\x00\x00\x00\x00\xBB\x00\x00\x00\x00\x00\x00\x00\x00\xEE�

�\xFF\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00�

##### 6. After executing the symbolic maze, what was the data value of the �program� object? (Hint: it will be a string of the lowercase letters **s**, **d**, **w**, and **a**.)

***sddwddddsddw***

##### 7. If you run the symbolic maze program so that it finds all solutions, not just one, how many are there?

***309 (But I think you have to work it yourself)***

##### 8. There was a bug in the maze program that allows the player to walk through walls. What line in maze-sym.cis the bug on? (If there are multiple lines, pick one of them.)
 ***113***