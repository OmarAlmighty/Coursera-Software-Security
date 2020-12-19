
# Week 4 quiz

##### 1. Why is waiting to think about security until after the software is built a bad idea?

 - ***All of the above***
 - Fixing problems once the software is built is more difficult and more
   expensive
 - You might miss important security requirements that necessitate a
   re-design
 - You might make critical mistakes in the software's design

##### 2. What is an abuse case?

 - An official report made by MITRE Corp that describes a discovered
   software vulnerability and possible abuse of it
 - ***A scenario that illustrates a potential failure in security under
   relevant circumstances***
 - An example of a heated disagreement between the security team and the
   development team
 - A scenario that illustrates a system's functional requirements

##### 3. Which of the following is a reason to make an explicit threat model when designing a system?

 - So that you avoid an incoherent defense
 - So you can defend against the most likely/costly/important attacks
 - So you can explicitly list and challenge assumptions that underlie your design
 - ***All of the above***
 
 ##### 4. Suppose you design software for a bank and the bank's customers may remotely log into its site using commodity PCs. These PCs might have malware on them, which could log keystrokes or read files stored on the machine. Which threat model (using terms defined in the lectures) makes the most sense for you to consider, when designing the bank's site?
 - Malicious user
 - ***Co-located user***
 - Network user
 - Snooping user

##### 5. What is a good defense against powers that are particular to a snooping user?

 - ***Using encryption***
 - Using a firewall
 - Using passwords to authenticate users
 - Using a type-safe language

 ##### 6. A denial of service attack violates what security policy/goal?

 - Integrity

 - ***Availability***

 - Authorization

 - Authentication
 
 ##### 7. When talking about computer security, what do we mean by the term, principal?

 - ***An actor, or role, that is the subject of a security policy***

 - A rule of thumb for secure coding

 - A method for delegation

 - A foundational observation
 
 ##### 8. Passwords, biometrics, and user-owned SMS-receiving mobile phones are useful for what security mechanism?

 - Small trusted computing base (TCB)

 - Audit

 - Authorization

 - ***Authentication***
 
 ##### 9. We identified several categories of secure design principles, with respect to how they deal with attacks. Running each browser tab in a separate OS process (as done by the Chrome browser) is an example of which category?

 - Prevention (of an attack)

 - ***Mitigation (of the damage from an attack)***

 - Recovery (from a successful attack)

 - None of the above
 
 ##### 10. Suppose you are implementing a graphical user interface for interacting with an implementation of the RSA cryptosystem, and you want to give users a way to generate new keys. Which of the following designs most takes security into account?

 - ***Allow the user to use a slider to choose the number of bits, setting
   slider initially to point at 2048 bits. As the user moves the slider
   to larger or smaller values, visualize the difference in relative
   protective power, e.g., using a meter.***

 - Use a text box to ask the user to fill in how many bits they want
   their key to be

 - Don't ask the user about key size at all -- always use 256 bits

 - Ask the user, but set the default response to be 2048 bits, which is
   chosen based on the assumption of a strong adversary
 
 ##### 11. Suppose you are implementing an extensible data management system. You want to accommodate plug-ins that can implement storage rules and query processing functionality for different data formats (e.g., relational data, object data, XML data, etc.). Which of the following designs most takes security into account?

 - The plug-ins and the main data management software are linked into
   the operating system kernel as a special kind of device driver, to
   give them direct access to stable storage and the network stack,
   while the OS can enforce their security

 - The plug-ins are linked directly in the address space of the data
   management software, ensuring high performance

 - ***The plug-ins are implemented as separate OS processes; these
   processes communicate to/from the main process to handle
   queries/updates for the data formats they support***

 - The plug-ins are implemented as separate OS processes but which share
   memory with the main process (and may access its memory as well), for
   better efficiency. Queries/updates occur via inter-process
   communication.
 
 ##### 13. Promoting privacy is a goal that follows from which category of secure design principle?

 - ***It is an example of trusting with reluctance because promoting
   privacy means sharing private information with as few software
   components as possible, meaning that fewer need to be trusted to
   protect the information***

 - It is an example of defense in depth because privacy is a deep topic
   that is often debated.

 - It is an example of monitoring and recovery because failure to
   promote privacy could be discovered by monitoring

 - It is an example of favoring simplicity because privacy is quite
   simply the right thing to do
 
 ##### 13. Encrypting a password database is an example of what category of design principle?

 - ***It is an example of defense in depth***

 - It is an example of favoring simplicity

 - It is an example of monitoring and recovery

##### 14. Which of the following vulnerabilities can VSFTPD's secure string library help protect against?

 - Privilege escalation
 - ***Buffer overflow***
 - ***Integer overflow***
 
 ##### 15. VSFTPD forks a new process to handle each client connection. It could have, instead, spawned a thread within the main process to handle each connection, as is done in many servers. How would this alternative design compare to the original?
 - ***It would be less secure because a compromise by a malicious client in
   one thread could (more easily) access data used by another client's
   thread, since they share the same address space***
 - It would be equally secure and would perform better because threads
   are cheaper to manage than processes
 - It would be more secure because threads are not subject to denial of
   service attacks but processes are
 - It would be more secure because we could apply the SecComp system
   call to these threads, but could not do so for processes
 
 ##### 16. FTP servers can be asked to list a directory of files. VSFTPD could do this by calling the system's ls (or dir) command, displaying the result to a client. But VSFTPD does not do this, and implements directory listings using the relevant system calls directly. Why might you argue that VSFTPD's design makes sense from a security perspective?
 - ***ls does more than is needed, and thus unnecessarily expands the TCB***
 - Calling ls involves forking a new process, which is less secure than
   running within the same process
 - Calling ls doesn't give us any way to employ fail-safe defaults
 - Using ls provides less control over the output, which leaves users
   open to XSS-style attacks
