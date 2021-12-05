# Task 1: Getting Familiar with Shellcode

The goal of a buffer overflow attack is to inject code into the target program, executing it with total privileges. Shellcode is the most widely used in order to do this. All it does, is launch a shell into the target program.

Shellcode is usually written in plain assembly language, and it is shipped as such. It is quite a non-trivial job and has some weird quirks to it, mainly concerned with security measures. The shellcode given, for instance, uses execve as a way to launch a shell, and passes the arguments given as well.

When the given shellcode is executed with the help of the Makefile, two binary object files are generated. One for 32 bit systems and one for 64. When executed, both launch a dedicated shell (with limited environment variables), and with the user's privileges given.

# Task 2: Understanding the Vulnerable Program

The binary files launch a shell because of a buffer overflow vulnerability found in the stack.c program. Since the strcpy function does not check bounds when copying, overflow will occur, and things will be written where they shouldn't. The payload is delivered through a file called badfile, which injects the malicious code in the memory area that sits above the stack.

When compiled, the Makefile will generate several stack.c variants, all of which become viable Set-UID programs.

# Task 3: Launching Attack on 32-bit Program

In order to exploit the stack vulnerability, it is essential to know the buffer's starting address and the location of the return address.

To find them out, the GNU debugger was used to give the exact address. It i important to note that since gdb was being executed as well, the position is not the exact same, as the gdb program pushed some values into the stack before running the program. As such, the actual frame pointer will be different.

Finally, to exploit the vulnerability, a payload must be constructed, as a means to store it into "badfile". To do this, the exploit.py file given must be altered. Here are the changes made:

1. The shellcode was copied with the desired architecture (in this case, 32bit systems)
2. The start address was defined to be the beggining of the buffer (this is irrelevant, as long as the return address points to the starting value)
3. The desired return address was given. In this case, we wanted the beggining of the buffer, where our shellcode resides. To find it, the gdb program was used, breaking at the function where the buffer was used (bof).       
4. After finding the desired return address, an offset was added. This offset takes into account the size of the buffer, the frame pointer and the return address. By making the difference, we found out where in the stack we needed to write the return address. 
5. Finally, when replicating the environment where the addresses where found (that is, by running the stack-L1-dbg program in the gdb), a shell was launched which included root privileges.

After quitting the gdb program, the shell persists and so do the privileges, which would allow the attacker to execute whatever they want.
