
# Week 1 Qualifying Quiz
This test is meant to test your knowledge of C programming and some basic computer science-related skills you will need to do well in this class. The outcome of the test is for your use only; it will not affect whether you can register for the class, and it will not apply to your grade if you do register. As such, we recommend that you do not research the answers on the Internet, but answer the questions to your best recollection.

##### 1. Consider the following variable declaration for bar in the function foo

```sh
void foo() {
  char bar[128];
  ...
}
```
Which of the following are true?

* ***Holds 128 elements***
* bar[1] contains the first element
* All elements are initialized to 0

#####  2. Consider the following code fragment: sizeof(int*) == sizeof(int). Which one of the following is true about it?

* This fragment will not compile 
* This fragment always evaluates to 0 (assuming it doesn't crash) 
* This fragment always evaluates to 1 (assuming it doesn't crash) 
* ***This fragment's result depends on the compiler and architecture***
* This fragment will always crash

##### 3. Suppose you are compiling for a 32-bit platform and sizeof(int) == 4. Which one of the following is equivalent to c[b] if c is of type int* and b is of type int?

* none of the above
* -1 * b[c] 
* *c+b 
* c[b][0] 
* ****(c+b)*** 

##### 4. Consider the following program.
```sh
#include <string.h>

int foo(void) {
  char bar[128];
  char *baz = &bar[0];
  baz[127] = 0;
  return strlen(baz);
}
```
What are possible outcomes from running this function? Check all that apply (note that the outcomes shown are not exhaustive):

* returns -1
* ***returns 127*** 
* returns 128 
* ***returns 0*** 
* crash 

##### 5. Consider the following code fragment.
```sh
char blah[] = "fizzbuzz";
printf("%s\n", blah+4);
```
What happens if we try to compile and run this code?

* ***The program outputs "buzz"*** 
* The program outputs a blank line depending on the size of pointers
* The program is illegal C and may not compile
* The program outputs "fizz"

##### 6. Which of the following are true of memory returned via the malloc function? Check all that apply.

* ***It must be manually released by the programmer*** 
* The memory is zero-initialized
* It is write-only
* It is automatically released by the operating system when the pointer to which the memory is assigned goes out of scope

##### 7. Consider the following code
```sh
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
  unsigned int i;
  unsigned int k = atoi(argv[1]);
  char *buf = malloc(k); /* 1 */
  if(buf == 0) {
    return -1;
  }

  for(i = 0; i < k; i++) {
    buf[i] = argv[2][i]; /* 2 */
  }

  printf("%s\n", buf); /* 3 */

  return -1;
}
```
* This program could crash at position 3
* ***This program could crash at 2 and 3*** 
* This program could crash at 1 and 2 
* This program could crash at position 2
* This program could crash at position 1
* This program could crash at all 3 positions 

##### 8. Which of the following are true statements about the program stack?

* It is used to store global variables while executing a function 
* It is used as the source of memory returned by malloc() 
* ***It is used to store local variables while executing a function*** 
* ***The stack is managed by code emitted by the compiler*** 
* Management of the stack is handled automatically by the architecture 

##### 9. Which of the following are true of the X86 call instruction?

* ***Branches to a specified address*** 
* ***Its target address may be specified in a general-purpose register*** 
* ***Pushes the instruction pointer value onto the stack*** 
* Pushes flag registers onto the stack 

##### 10. Consider the following program
```sh
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[]) {
  int **blah2 = malloc(sizeof(int*)*N);
  int *special = NULL;
  int i, j;

  for(i = 0; i < N; i++) {
    int *tmp = (int *)malloc(sizeof(int)*M);
    memset((void *)tmp, 0, sizeof(int)*M);
    if(i > N) {
      special = &tmp[3];
    }
    blah2[i] = tmp;
  }

  if(special != NULL) {
    *special = 7;
  }

  for(i = 0; i < N; i++) {
    for(j = 0; j < M; j++) {
      printf("%d ", blah2[i][j]);
    }
    printf("\n");
  }

  return 0;
}
```
Assuming we #define N and M to be positive integers, and the calls to malloc() succeed (the arguments do not overflow, and do not return NULL), then which of the following is true?
* This program crashes
* This program outputs a matrix with at least one element being 7 
* This program outputs a random NxM matrix
* ***This program outputs a zero NxM matrix*** 
* This is not a valid C program

##### 11. What is TCP?

* It is connectionless
* It ensures data confidentiality
* ***It is a protocol that supports reliable data transfer on the Internet*** 
* It is a protocol often implemented on top of HTTP

##### 12. What is PHP? Pick one.

* The acronym for a coding standard
* A programming language often used to implement network switches
* A network protocol
* ***A programming language often used to implement web sites*** 

##### 13. Which of the following statements about HTML are true?
* ***Web browsers render HTML content served by web sites*** 
* HTML is a kind of URL
* ***HTML documents have tags that identify different sorts of data*** 
* ***HTML is a text-based format (as opposed to a binary format)***

##### 14. What is gcc?

* All of the above
* An interpreter
* A virtual machine
* ***A compiler***

##### 15. The shell command cd; ls *.xml

* Will list all files ending in the xml suffix in the previous working directory
* Will list the file *.xml in the current directory
* ***Will list all files ending in the xml suffix in user's home directory*** 
* Will list all of the files listed in the given XML file
