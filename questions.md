# **Task 2: Answer the following questions**



1. OS/161 needs to be reconfigured every time a new file is added to the system either in `kernel` "land" or `userland`. What the path of the directory where the configuration files are kept? 

   ```shell
   I believe that the configuration files are stored in the directory ~/kern/conf
   ```

2. The `trapframe` data structure describes what is saved on the stack during entry to the exception handler. The address of this data structure is passed as an (input) argument to the various trap/interrupt handlers in the system. What is the path of the directory containing the `trapframe` definition? 

   ```shell
   The trapframe is stored in the directory kern/arch/mips/include
   ```

3. Which file contains the definition of the system call IDs in OS/161? Write the path to the file (including the filename).

   ```shell
   The system call IDs are kept in a file called systemcall.h It is located in the directory kern/include/kern/systemcall.h
   ```

4. The assembly program `kern/arch/mips/locore/exception-mips1.S` is called when a trap/interrupt occurs. What is the instruction that calls the trap handler (.c program)? Write the instruction. 

   ```shell
   jal mips_trap
   ```

5. What is the path to the file where the function `mips_trap()` is implemented? 

   ```shell
   /kern/arch/mips/locore/trap.c
   ```

6. What is the path of the file where the function `mips_trap()` is implemented? 

   ```shell
   /kern/arch/mips/locore/trap.c
   ```

7. In the file that contains `mips_trap()`, what is the line number where the system-call handler is invoked? 

   ```shell
   syscall(tf) is called on line 224, the if statement to activate it is on line 216
   ```

8. What is the path of the file where the system-call handler is implemented? 

   ```shell
   kern/arch/mips/syscall/syscall.c
   ```

9. What field of `trapframe` is used to pass the ID of the system call being requested to the system-call handler? 

   ```c
   tf->tf_v0, tf->tf_a0, tf->tf_a1, tf->tf_a2, tf->tf_a. Out of these fields, I think it is tf_v0
   ```

10. In the system-call handler, which variable indicates whether the system call completed successfully?

    ```c
    It is the int variable 'err' that indicates whether a system call is successful in syscall.c
    ```

11. What value is used to indicate the successful completion of system calls? 

    ```c
    If a syscall is successful, it sets tf_a3 = 0. This represents a successful completion
    ```

12. In the system-call handler, which variable is used to store the return result of a system call other than its success status? 

    ```c
    retval
    ```

13. What the path of the directory where the implementation (i.e., `.c` files) of system calls are kept? 

    ```c
    /kern/syscall
    ```

14. What are the directories inside `userland/testbin/` ? 

    ```shell
    The directories inside of userland/testbin/ are used to test the system calls that we make. They stress-test the system.
    ```

15. What is the goal of the file: `userland/testbin/Makefile`? 

    ```shell
    The goal of this file is to act as a recursive build controller for all of the programs that are within the testbin directory.
    ```

16. Consider lines 6, 7, and 8 in the file `userland/testbin/forktest/Makefile`. What does each line do? 

    ```shell
    These lines are responsible for controlling how the forktest 'test' is compiled and linked.
    line 6: PROG=forktest tells the system that once the build is compiled, to name it forktest.
    line 7: SRCS=forktest.c tells the system the source files needed for the build.
    line 8: BINDIR =/testbin tells the system where to put the installation files.
    ```
