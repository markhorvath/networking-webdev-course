* Networking for Web Developers Course Notes

### Lesson 1

    * printf 'HEAD / HTTP/1.1\r\nHost: en.wikipedia.org\r\n\r\n' | nc en.wikipedia.org 80
    * printf is kind of like echo, prints stuff in shell, it can turn \n into line break
    * nc = netcat, tool for talking to internet services, sort of a network swiss army knife to connect to various servers, eg. nc localhost 22 returns info on local host
    * | or "pipe", tells computer to take output from preceding program and feed it as input to succeeding program

Layer | Protocol | Concepts
---   |  :---:     | ----
Application | HTTP, SSH | URLs, passwords
Transport | TCP, UDP | port numbers, sessions
Internet | IP | IP addresses, routes
Hardware | wifi, ethernet, DSL | signal strength, access points

    * man nc (brings up manual for netcat)
    * nc -l #### (#### is a port number to listen to), (think '-l' for 'listen')
    * rst = reset packet, this is an error message for a call to a port that isnt listening
    * Open to shells, nc -l 3456 in one, nc localhost 3456 in the other, these two are now connected and can transfer data, this is a TCP server (one layer below a web server), TCP is like a two way road where both ends can talk to each other and send data at the same time
    * ctrl-C or ctrl-D to exit (ctrl-D sends the standard Unix signal for 'end of input')
    * printf "GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n" | nc www.example.com 80 (GET request)
    * to save the results of a nc command, add a '> filename.txt' at the end like so:
    * printf "GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n" | nc www.example.com 80 > example.txt
    * the port number range nc can listen to is 1024 to 65535, or down to 1 if using sudo
    * normally one program can listen on a given port on a machine at a time, but once a program starts it can run threads and child processes that handle incoming connections on a port or loop between several connections and handle all of them, which is what a normal web server does, not nc -l
    * lsof (Lists Open Files), or sudo lsof -i #### which will list only network sockets
    * nc -l 2345, then open browser and go to your IP address with :2345 at the end,
    * printf 'HTTP/1.1 302 Moved\r\nLocation: https://www.eff.org/' | nc -l 2345  in ssh to send a return response, which should print the redirect info and the browser should show the page www.eff.org

