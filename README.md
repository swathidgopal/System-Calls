# System-Calls

User applications use system calls to request some service or resource from the operating system. When
system calls are used, the kernel is invoked via a special trap, or software interrupt (depending on the CPU
architecture). Some common system calls include read() and write() which are used when reading and writing
from/to a file. The kernel needs to be involved as is has to ensure that the user application has the proper
permissions needed to read and write that file. The system call getpid() is another simple system call that
requests from the the process id of the calling process. This sort of functionality is handled by the kernel as
the kernel is responsible for managing processes and assigning their IDs. Given that system calls require the
kernel to carry out the request before the user application can continue executing, it can incur significant
overheads if we use system calls often.
