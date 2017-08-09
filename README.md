* Networking for Web Developers Course Notes

***

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