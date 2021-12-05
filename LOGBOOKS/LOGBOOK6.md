# Task 1

This task introduces us to the environment we will be working on. We start by running a shell on one of the servers created by the docker-compose.yml file.

This shell will run the malicous code, and the results will be echoed by Docker to the terminal that is running them in the background.
The sent string can be of any type, and since the program does no sort of check, the right string can cause a program crash.
For example, we can write a %s in the format string, which tries to look for a place in memory to read it as a string. Also, a %n can be used, which does the inverse, and tries to write in memory some sort of memory value. The problem with this is that, in the case of the memory value being invalid, the program will halt and crash, since it cannot read or write from it, causing a kind of DoS attack on the program.

# Task 2

## Task 2.A: Stack Data

To print the first four bytes of our input, we needed to use '%x' 64 times. For this we gave the program an easy to identify sequence of 4 chars ("AAAA") and secondly found it in hexadecimal, in the output of the function given by the usage of multiple %x, and counted the number of addresses until one corresponded to our number.

## Task 2b.

For this task we had to write the address 0xffffdfc0 in the first byte, and then %64.s right after. How we found the exact number '64' was by printing the addresses until the address was equal to the beginning of the buffer.

# Task 3

## Task 3A.

This task was very similiar to the last one, we still had to write an address at the beginning of the buffer, and use the same offset 64, but instead of  %64$.s, we write %64$.n  and %x %x to see if the variable was changed, and it was succesfull, it's value is now 4.

## Task 3B.

%n writes the into the memory address the number of bytes written thus far, so we just have to write 0x5000 bytes before the %n. To achieve this, we just add %1$.20476x before the %64$.n, and it's value is changed to 0x5000.
