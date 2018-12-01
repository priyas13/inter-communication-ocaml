## Processes 
A process is a program executing on the operating system. Inside a program there can be multiple processes running at a time.
```
val fork : unit -> unit 
```
* A new child is created from the parent processe using *_fork_* function. 
```
val getpid : unit -> unit 
```
* A process can obtain its own process id by *_getpid_*.
```
val getppid : unit -> unit
```
* A process can obtain its parent's id by *_getppid_*.
* A child process is initially at the same state as the parent's state. The state is not shared between the parent and the child 
but initially when the child process is forked from the parent process, it gets the same state as the parent process. For example, if there 
is a variable bound to a reference before the fork, a copy of that reference and its current contents is made at the moment of fork. After 
the fork, the child process and the parent process both independently modifies its "own" reference without affecting the other process.
```
val wait : unit -> int * process_status
```
* A process can terminate using wait. Parent process waits until one of the children processes die, and return its pid and termination status.
Type int denotes the id. The process status can be of these three type:
![process_status](https://github.com/priyas13/inter-communication-ocaml/blob/master/process-status.png)
* All the processes are stored in the process table. But when a process is terminated by the parent process by calling wait, after
returning the value, the process is removed from the process table.
* Processes are *_preemptive_* in nature (unlike *_threads_*), which means that the execution of processes is entrusted to a particular process.
A process cannot determine the time of its execution.
* Processes have their unique id and thier own private memory space which can communicate via files or communication channels.
*_Distributed memory model of parallelism is simulated on a single machine_* 
