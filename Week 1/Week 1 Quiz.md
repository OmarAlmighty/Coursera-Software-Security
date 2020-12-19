# Week 1 quiz

##### 1. Three of the following are classic security properties; which one is not?

 - Availability
 - Confidentiality
 - ***Correctness***
 - Integrity

##### 2. What was the first buffer overflow attack?

 - Love Bug
 - SQL Slammer
 - ***Morris Worm***
 - Code Red

##### 3. The stack is memory for storing

 - ***Local variables***
 - Program code
 - Dynamically linked libraries
 - Global variables

##### 4. Why is it that the compiler does not know the absolute address of a local variable?

 - Programs are not allowed to reference memory using absolute addresses
 - The size of the address depends on the architecture the program will
   run on
 - ***As a stack-allocated variable, it could have different addresses
   depending on when its containing function is called***
 - Compiler writers are not very good at that sort of thing

##### 5. When does a buffer overflow occur, generally speaking?

 - when writing to a pointer that has been freed
 - when copying a buffer from the stack to the heap
 - ***when a pointer is used to access memory not allocated to it***
 - when the program notices a buffer has filled up, and so starts to
   reject requests

##### 6. How does a buffer overflow on the stack facilitate running attacker-injected code?

 - ***By overwriting the return address to point to the location of that
   code***
 - By writing directly to the instruction pointer register the address
   of the code
 - By writing directly to %eax the address of the code
 - By changing the name of the running executable, stored on the stack

##### 7. What is a nop sled?

 - It is an anonymous version of a mop sled
 - ***It is a sequence of nops preceding injected shellcode, useful when
   the return address is unknown***
 - It is a method of removing zero bytes from shellcode
 - It is another name for a branch instruction at the end of sequence of
   nops

##### 8. The following program is vulnerable to a buffer overflow (assuming the absence of automated defenses like ASLR, DEP, etc., which we introduce in the next unit). What is the name of the buffer that can be overflowed?
```sh
#include <stdio.h>

#include <string.h>

#define S 100

#define N 1000

int main(int argc, char *argv[]) {

char out[S];

char buf[N];

char msg[] = "Welcome to the argument echoing program\n";

int len = 0;

buf[0] = '\0';

printf(msg);

while (argc) {

sprintf(out, "argument %d is %s\n", argc-1, argv[argc-1]);

argc--;

strncat(buf,out,sizeof(buf)-len-1);

len = strlen(buf);

}

printf("%s",buf);

return 0;

}
```

 - ***out***
 - len
 - buf
 - msg

##### 9. Here is the same program as the previous question. What line of code can overflow the vulnerable buffer?
```sh
#include <stdio.h>

#include <string.h>

#define S 100

#define N 1000

int main(int argc, char *argv[]) {

char out[S];

char buf[N];

char msg[] = "Welcome to the argument echoing program\n";

int len = 0;

buf[0] = '\0';

printf(msg);

while (argc) {

sprintf(out, "argument %d is %s\n", argc-1, argv[argc-1]);

argc--;

strncat(buf,out,sizeof(buf)-len-1);

len = strlen(buf);

}

printf("%s",buf);

return 0;

}
```

 - ***sprintf(out, "argument %d is %s\n", argc-1, argv[argc-1]);***
 - printf(msg)
 - len = strlen(buf);
 - strncat(buf,out,sizeof(buf)-len-1);
 - printf("%s",buf);

##### 10. Recall the vulnerable overflow from the previous two questions. We can change one line of code and make the buffer overrun go away. Which of the following one-line changes, on its own, will eliminate the vulnerability?
```sh
#include <stdio.h>

#include <string.h>

#define S 100

#define N 1000

int main(int argc,char *argv[]) {

char out[S];

char buf[N];

char msg[] = "Welcome to the argument echoing program\n";

int len = 0;

buf[0] = '\0';

printf(msg);

while (argc) {

sprintf(out,"argument %d is %s\n",argc-1,argv[argc-1]);

argc--;

strncat(buf,out,sizeof(buf)-len-1);

len = strlen(buf);

}

printf("%s",buf);

return 0;

}
```

 - change printf("%s",buf) to printf(buf);
 - change printf(msg) to printf("%s",msg);
 - change char msg[] = "Welcome to the argument echoing program\n" to
   char msg[42] = "Welcome to the argument echoing program\n"
 - ***change sprintf(out, "argument %d is %s\n", argc-1, argv[argc-1]) to
   snprintf(out, S, "argument %d is %s\n", argc-1, argv[argc-1])***

##### 11. Recall the vulnerable program from the previous few questions. Which of the following attacks do you think the program is susceptible to?
```sh
#include <stdio.h>

#include <string.h>

#define S 100

#define N 1000

int main(int argc, char *argv[]) {

char out[S];

char buf[N];

char msg[] = "Welcome to the argument echoing program\n";

int len = 0;

buf[0] = '\0';

printf(msg);

while (argc) {

sprintf(out, "argument %d is %s\n", argc-1, argv[argc-1]);

argc--;

strncat(buf,out,sizeof(buf)-len-1);

len = strlen(buf);

}

printf("%s",buf);

return 0;

}
```

 - code injection
 - data corruption
 - reading arbitrary addresses in memory
 - ***all of the above***

##### 12. Recall the program again.
```sh
#include <stdio.h>

#include <string.h>

#define S 100

#define N 1000

int main(int argc, char *argv[]) {

char out[S];

char buf[N];

char msg[] = "Welcome to the argument echoing program\n";

int len = 0;

buf[0] = '\0';

printf(msg);

while (argc) {

sprintf(out, "argument %d is %s\n", argc-1, argv[argc-1]);

argc--;

strncat(buf,out,sizeof(buf)-len-1);

len = strlen(buf);

}

printf("%s",buf);

return 0;

}
```
If we changed printf("%s",buf) to printf(buf) then the program would be vulnerable to what sort of attack?

 - heap overflow
 - ***format string attack***
 - use-after-free attack
 - all of the above

##### 13. Exploitation of the Heartbleed bug permits

 - overwriting cryptographic keys in memory
 - a kind of code injection
 - ***a read outside bounds of a buffer***
 - a format string attack

##### 14. Why is it that anti-virus scanners would not have found an exploitation of Heartbleed?

 - It's a vacuous question: Heartbleed only reads outside a buffer, so
   there is no possible exploit
 - ***Anti-virus scanners tend to look for viruses and other malicious
 code, but Heartbleed exploits steal secrets without injecting any
   code***
 - Heartbleed exploits are easily mutated so the files they leave
 - behind do not appear unusual
 - Heartbleed attacks the anti-virus scanner itself

##### 15. An integer overflow occurs when

 - ***an integer expression's result "wraps around"; instead of creating a
   very large number, a very small (or negative) number ends up getting
   created***
 - an integer is used as if it was a pointer
 - an integer is used to access a buffer outside of the buffer's bounds
 - there is no more space to hold integers in the program
