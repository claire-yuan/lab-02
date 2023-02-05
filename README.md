# Lab 2
[Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repo and clone it to your machine to get started!

## Team Members
- Claire Yuan
- June Shao

## Lab Question Answers

Question A.1: 
Around 3 or 4 numbers out of 10 were not received by the server. This is because UDP does not verify that data packets are received by the server, so some may be lost.

Question A.2:
No packets were lost over TCP, since the protocol ensures that segments are received in the proper order. If any one is missing, the server waits. 

Question A.3:
The TCP response became slower after forcing a 50% loss. Sometimes there were pauses, likely because a lost packet was detected and needed to be retransmitted.

## tcp_server.c Answers

Question C.1
Arguments can be added when executing the program in the command line, so *argv[] contains these argument and passes them to main. The type is an array of char pointers. argc, the first parameter, is an int that indicates the length of the array.

Question C.2
A UNIX file designator is a unique positive integer used to identify an open file in the OS. The file descriptor table maps the integer to a data structure representing the actual file connection. (Source: https://www.usna.edu/Users/cs/wcbrown/courses/IC221/classes/L09/Class.html)

Question C.3
A struct is a custom data type with member variables and functions.
sock_addrin consists of short sin_family (the protocol family), unsigned short sin_port (port number), struct in_addr sin_addr (which contains the host IP address), and char sin_zero[8] (which can be set to 0). (https://www.gta.ufrj.br/ensino/eel878/sockets/sockaddr_inman.html)

Question C.4
The input parameters of socket() are the communication domain / protocol family, socket type (e.g., SOCK_STREAM), and protocol (0 if the only protocol in the family). socket() returns the file descriptor of the created socket or -1 if there is an error. (https://man7.org/linux/man-pages/man2/socket.2.html)

Question C.5
bind() takes in the file descriptor of the socket, a pointer to the sockaddr struct containing the address to be bound to the socket, and the size of the address. (https://pubs.opengroup.org/onlinepubs/009695399/functions/bind.html)
listen() requires a sockfd parameter (to mark the socket as passive) and a backlog parameter, which is the maximum number of pending connections to be accepted in the queue. (https://man7.org/linux/man-pages/man2/listen.2.html)

Question C.6
If there are multiple connections in the queue, while(1) allows you to handle one after the other. One problem that may occur is that if there are too many connections, this may be slow. Also, if the number of connnection exceeds the backlog size, new connections after that would not be accepted. 

Question C.7
fork() creates a child process that runs in parallel with the parent process. This is more efficient, as child processes are able to handle multiple connections while the parent process accepts new connections. (https://stackoverflow.com/questions/6014055/how-is-socket-connection-being-handled-in-a-forked-process)

Question C.8
A system call is a program's request of a service from the operating system.
