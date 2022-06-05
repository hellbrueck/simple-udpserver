# simple-udpserver

to build and run a simple udp server just use ncat wirh option -u for udp. see https://nmap.org/ncat/

for echo server run

	ncat -v -e /bin/cat -k -u -l 11211

to connect it to the bash and have it run as kind of telnet server (based on udp) run

	ncat -v -e /bin/bash -k -u -l 11212

if you do not want to install ncat use the dockerized versions in docker hub https://hub.docker.com/
