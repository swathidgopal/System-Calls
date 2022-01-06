# System-Calls
Measuring the cost of getpid and read system calls
User applications use system calls to request some service or resource from the operating system. When
system calls are used, the kernel is invoked via a special trap, or software interrupt (depending on the CPU
architecture). Some common system calls include read() and write() which are used when reading and writing
from/to a file. The kernel needs to be involved as is has to ensure that the user application has the proper
permissions needed to read and write that file. The system call getpid() is another simple system call that
requests from the the process id of the calling process. This sort of functionality is handled by the kernel as
the kernel is responsible for managing processes and assigning their IDs. Given that system calls require the
kernel to carry out the request before the user application can continue executing, it can incur significant
overheads if we use system calls often.
# Signal Handler
Signaling is important aspect of Interprocess Communication (IPC). A signal is a mechanism used for
delivering an asynchronous event or notification to a process. Common reasons for a process to receive a
signal are memory protection violations (SIGSEGV), divide by zero error (SIGFPE), and an expired timer
(SIGALRM). Signals interrupt the normal flow of execution of a program and are generally handled by a
signal handler function. User programs can also register a signal handler, which gives the user program the
ability to try and handle a signal in a specific way.

In the skeleton code - sigHandler.c, void floating_point_exception_handler(int signum) – the signal handler
will be called on any segmentation violation in this program. divided by zero is pretty much guaranteed to do
that. Linux will first run your signal handler to give you a chance to address the floating point exception. If
you return from the signal handler and the same signal occurs, then Linux will stop your code with a floating
point exception. You must, in the signal handler only, make sure the floating point exception does not occur
a second time. The problem is that Linux will attempt to run the offending instruction again. So you must
somehow make it not run that instruction. The key to doing this is the signal number. What you need to
do in this programming assignment is adding codes in the signal handler that causes the program to run to
completion.
