In **Linux**, a _data stream_ refers to the flow of bytes between processes or between a process and a file, device, or network connection. Streams are a fundamental part of Linux’s **input/output (I/O) model**, which treats everything — files, devices, and even network sockets — as a file that can be read from or written to. 
###  Types of Standard Data Streams

Every process in Linux has **three standard data streams**, created by default when the process starts:

| Stream                       | File Descriptor | Direction | Default Device | Description                                         |
| ---------------------------- | --------------- | --------- | -------------- | --------------------------------------------------- |
| **stdin** (standard input)   | 0               | Input     | Keyboard       | Used to take input from the user or another process |
| **stdout** (standard output) | 1               | Output    | Terminal       | Used to display normal program output               |
| **stderr** (standard error)  | 2               | Output    | Terminal       | Used to display error messages                      |
anything you write to your terminal is  **stdin** given to the shell to be executed, and anything comes from the shell to the terminal could be **stdout** or **stderr** 

### How Streams Work

Streams allow **inter-process communication (IPC)** and **data redirection**. For example:

1. Redirect stdout to a file 
`ls > output.txt`  

2. Redirect stderr to a file 
`ls nonexistentfile 2> error.log`

3. Redirect both stdout and stderr
`ls /etc /fake  > all_output.txt 2>&1`  

4. Use a pipe to send stdout of one process to stdin of another 
`cat file.txt | grep "keyword"`

Note: 
**`> or 1>`** redirects standard output.
**`2>`** redirects standard error.
**`|` (pipe)** connects the output stream of one process to the input stream of another.


###  File Descriptors and Streams

Each stream is associated with a **file descriptor (FD)** — a small integer that uniquely identifies an open file or data channel for a process.

| FD  | Name   | Description         |
| --- | ------ | ------------------- |
| 0   | stdin  | Input stream        |
| 1   | stdout | Output stream       |
| 2   | stderr | Error output stream |
### Why we need the File Descriptors ( FD )
1. **Uniform I/O Interface (“Everything is a file”)**
Linux treats _everything_ — files, devices, pipes, sockets — as a file.  
By assigning a file descriptor to each, the kernel can use the same **read()** and **write()** system calls for all types of data streams.

2. **Efficient Process Management**
Each process has its own **file descriptor table**, which maps FDs to kernel-managed file structures.  
When you duplicate or redirect streams (like with `2>&1`), the kernel just updates pointers — no need to copy file data.

3. **Redirection and Piping**
Redirection (`>`, `<`, `2>`) and pipes (`|`) work _by manipulating file descriptors_.

4. **Multiplexing I/O (select, poll, epoll)**
File descriptors also enable efficient **I/O multiplexing**, where a process can monitor multiple streams simultaneously.

Note: 
there is a huge difference between `>` and `>>`
`>` means **overwrites** the existing one.
`>>` **adds** to the end of the existing one.