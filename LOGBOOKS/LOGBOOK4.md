# Task 1

- The printenv and env commands display all of the system's environment variables, which gives the operating system some notions about the state of operation.

- Export and unset are Bash-specific commands that allow the user to remove environment variables at will.

# Task 2

After executing the task's steps, namely the diff command to see the difference between the two outputs that were saved in files, it is possible to see that there is no difference between the parent and the child's environment variables. As such, we can conclude that the child process inherits the environment variables from the parent.

# Task 3

- After executing the first step of the task, no environment variables showed up. This means that execve only passes the environment variables that are given as a third argument, and since we sent out NULL, none existed.

- And when the second part is done, we can see that now the environment variables show up, meaning that they are stored in the environ variable.

# Task 4

With this task we can easily check that when the system function calls the system's shell, it also passes the environment variables down to the called program.

# Task 5

In task 5, it is asked to try and see if the environment variables get into the Set-UID program. Well, since all the shell does in order to start the program is fork itself to run the program, and the program is then the child process of the shell, we can see from Task 2 that the environment will not change from parent to child process, and so they will remain the same in this program as well. 

# Task 6

The final task asks us to inject some malicious code by exploiting this vulnerability in the environment variables. As a way to fool naive users, a system call to ls was made, but by not specifying the absolute path, the program has to search through all the possible PATHS. As such, it traverses the recently modified PATH environment variable where a new place was injected. In that directory, it finds a function of name ls and executes that instead of the real one, that is located in /bin/ls instead. This way, we can inject any type of malicious code in the function body, and it will run just as ls would to the unsuspecting user.

Whilst there are now countless defenses built-in to fight against these types of attacks, it is still important to understand that such small details like the "environment" the OS is in can have such a big impact on the program.
