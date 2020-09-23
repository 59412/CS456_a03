Language: Python 3.6.1

Completed: All requirements are met including:
		server
		client
		Makefile

Makefile: 
	make all: do nothing since it's python script
	make clean: delete port

Testing Machine: @ubuntu1604-002%

Logic: 

The assignment is completed with multi-threading, the basic designs are:

Server: server keep track of a few things: 
	1. the list of pending downloaders
	2. Address for all these downloaders
	3. All current threads, which represent the connections where the files are being forwarded (transfer in progress)

	When server receive key from a downloader:
	1. it stores the key
	2. it stores the address of the downloader

	When server receive key from uploader:
	1. it matches the key to a downloader, and find the address of the downloader with the same key
	2. it creates a new thread, the thread will be working on forwarding the file from uploader to downloader

	When server receive a termination request:
	1. it deletes all pending downloaders
	2. it stops listening to requests
	3. it wait for all other threads to complete (finish all transfer in progress)
	4. server shuts down (close socket)