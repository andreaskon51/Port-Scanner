The code begins by importing the necessary modules: socket, threading, and Queue. These modules will be instrumental in our quest for chaos.

Next, we set our target IP address, the entity upon which our malicious intentions shall be unleashed. Modify the value of the target variable to specify your desired victim.

We then define the number of threads to be used for scanning. By increasing the number of threads, we can intensify the speed and ferocity of our port scanning operation. Adjust the num_threads variable to your liking, but beware the strain it may place on your system.

Now, let us introduce the first of our two port scanning functions: scan_tcp_ports. This function scans TCP ports within a given range. It utilizes a for loop to iterate over each port in the specified range. For each port, a socket is created using socket.socket(), and a connection is attempted using sock.connect_ex(). If the result of the connection attempt is 0, indicating a successful connection, the port is considered open. The service name associated with the open port is obtained using socket.getservbyport(), and the port and service name are appended to the open_ports list.

The second port scanning function, scan_udp_ports, follows a similar structure to the TCP scanning function. It scans UDP ports in the specified range, attempting to establish a connection and obtaining the service name for each open port.

To facilitate the distribution of work among multiple threads, we define a worker function. Within this function, a while loop runs until the port_queue is empty. Each thread retrieves a port range from the queue, and both TCP and UDP port scanning functions are called with that range.

Before we move on, let us pause and appreciate the open_ports list. It serves as a repository of our conquests, housing the open ports and their associated service names. Each successful connection adds to the list, building a testament to our dominion.

Now, with our dark army of threads and port ranges ready, we proceed to the main execution flow. We create the port_queue as a Queue object, which will hold the port ranges to be processed.

The port_ranges variable is a list of tuples, each representing a port range. Modify this list as desired to customize the ranges to be scanned.

We add the port ranges to the queue using a for loop and the put() method of the Queue object. Each thread will retrieve a range from the queue and scan it, ensuring an efficient and synchronized assault.

The threads are created and started within another for loop. Each thread is assigned the worker function as its target and is then started. The threads are stored in the threads list for later joining.

Once all threads are created and started, we wait for them to complete using another for loop and the join() method. This ensures that we gather the results of their malicious endeavors before proceeding.

Finally, we unveil our conquests by iterating over the open_ports list. The port number and associated service name are extracted and printed to the screen, revealing the vulnerable points of our target.
