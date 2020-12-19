# Week 6 quiz

##### 1. What is penetration testing?

* A procedure for testing libraries or other program components for vulnerabilities

* All of the above

* ***Whole-system testing for security flaws and bugs***

* A security-minded form of unit testing that applies early in the development process

##### 2. Which of the following are benefits of penetration testing?

* You can prove a positive: Penetration testing will establish your system is secure

* Compositionality of security properties means tested components are secure even if others change

* ***They specifically consider adversarial thinking, which is not usually necessary for normal tests***

* ***Results are often reproducible***

* ***Results are certain and not hypothetical***

##### 3. What does it mean to "be stealthy" during a penetration test?

* Performing the tests from an undisclosed location

* ***Taking care to avoid activities during a penetration test that might attract attention, e.g., by operators or IDS services***

* Using encryption during tests to make the source of attacks impossible to determine

* Performing penetration testing without the target organization knowing

##### 4. What is a web proxy?

* ***A piece of software that intercepts and possibly modifies requests (and responses) between a web browser and web server***

* An agent that makes decisions on the client's behalf when interacting with web applications

* A piece of software that makes a web application look like a standalone application, making it easier to test

* A simulator for the web, for use when off-line

##### 5. What is Nmap?

* ***It is a scanner which works by injecting packets to a range of addresses, and inferring what hosts and services might be at those addresses, based on the responses***

* It is a map of the Internet

* It is a network fuzz testing tool

* It is a suite of tools for scripting attacks: probe, construct, encode, inject, wait for response

##### 6. What is ethical hacking?

* Hacking into systems run by those whose ethics you disagree with

* "Hacking" ethics so they justify unintended selfish behavior

* ***Hacking systems (e.g., during penetration testing) to expose vulnerabilities so they can be fixed, rather than exploited***

* A slang term for rapid software development, e.g., as part of hackathons

##### 7. Which of the following statements describe fuzz testing (aka fuzzing)?

* ***It is concerned with finding known-bad behaviors, like crashes and hangs***

* It focuses on simple testing patterns and does not employ sophisticated analysis techniques

* It is always black-box, in being indifferent to the software's functionality

* ***It has been used to find security vulnerabilities in many commodity programs***

##### 8. Which of the following are true of whitebox fuzzing?

* ***It takes into account the program's internals in some manner when deciding which inputs to choose***
* ***American Fuzzy Lop is (at least in part) a whitebox fuzzer***

* Radamsa is (at least in part) a whitebox fuzzer

* ***SAGE is (at least in part) a whitebox fuzzer***

* It makes no sense to combine it with grammar-based fuzzing since the latter is just another way to consider the program's semantics

##### 9. Which of the following is true of mutation-based fuzzing?

* It only makes sense for file-based fuzzing, not network-based fuzzing

* Each input is mutation that follows a given grammar

* It works by making small mutations to the target program to induce faults

* ***It generates each different input by modifying a prior input***

##### 10. Which of the following styles of fuzzer is more likely to explore paths covering every line of code in the following program?
```sh
int main(int argc, char **argv) {
  char buf[100];
  while (fgets(buf,sizeof(buf),stdin) != NULL) {
    int c = atoi(buf);
    if (c == 456799)
      printf("%s\n",(char *)c);
    else {
      int i = 0;
      for (i=0; i<c; i++)
 printf(".");
      printf("\n");
    }
  }
  return 0;
}
```
* Blackbox

* ***Whitebox***

* Mutation-based

* Generational

##### 11. Which of the following are functions of a network-based fuzzer?

* Scanning a network address range

* ***Acting as a "man in the middle"***
* Acting as a client

* ***Acting as a server***

##### 12. Suppose you want to use fuzzing on a program to try to find memory errors; which of the following statements is true?

* Fuzzing doesn't find memory errors, it finds crashes and hangs

* You should not use a grammar-based fuzzer, because its adherence to the grammar means it will not find memory errors

* Compiling the program with address sanitizer (ASAN) will make errors harder to reproduce

* ***Compiling the program with address sanitizer (ASAN) will make the source of a memory error easier to find***
