# simple-udpserver

to build and run a simple udp server just use ncat wirh option -u for udp. see https://nmap.org/ncat/

for echo server run

	ncat -v -e /bin/cat -k -u -l 11211

to connect it to the bash and have it run as kind of telnet server (based on udp) run

	ncat -v -e /bin/bash -k -u -l 11212

if you do not want to install ncat use the dockerized versions in docker hub https://hub.docker.com/

if you do not want to install ncat use the dockerized versions in docker hub https://hub.docker.com/

	docker pull hellbruh/simple-udpserver
	
	docker run -it -p 11211:11211/udp hellbruh/simple-udpserver
	
you can kill and stop via Ctrl-P Ctrl-Q and docker stop (see below)

or build you own image with [Dockerfile](./docker/Dockerfile) [here](./docker) provided for the echo server (change directory to folder docker)

	docker build -t simple-udpserver .
	
	docker run -it -p 11211:11211/udp simple-udpserver

see the following output:

	hellbruh@PEP:/tmp/docker/simple-udpserver/docker$ docker build -t simple-udpserver .
	[+] Building 7.4s (6/6) FINISHED
	 => [internal] load build definition from Dockerfile                                                               0.3s
	 => => transferring dockerfile: 181B                                                                               0.1s
	 => [internal] load .dockerignore                                                                                  0.2s
	 => => transferring context: 2B                                                                                    0.0s
	 => [internal] load metadata for docker.io/library/alpine:latest                                                   2.8s
	 => [1/2] FROM docker.io/library/alpine:latest@sha256:686d8c9dfa6f3ccfc8230bc3178d23f84eeaf7e457f36f271ab1acc5301  1.5s
	 => => resolve docker.io/library/alpine:latest@sha256:686d8c9dfa6f3ccfc8230bc3178d23f84eeaf7e457f36f271ab1acc5301  0.1s
	 => => sha256:4ff3ca91275773af45cb4b0834e12b7eb47d1c18f770a0b151381cd227f4c253 528B / 528B                         0.0s
	 => => sha256:e66264b98777e12192600bf9b4d663655c98a090072e1bab49e233d7531d1294 1.47kB / 1.47kB                     0.0s
	 => => sha256:2408cc74d12b6cd092bb8b516ba7d5e290f485d3eb9672efc00f0583730179e8 2.80MB / 2.80MB                     0.8s
	 => => sha256:686d8c9dfa6f3ccfc8230bc3178d23f84eeaf7e457f36f271ab1acc53015037c 1.64kB / 1.64kB                     0.0s
	 => => extracting sha256:2408cc74d12b6cd092bb8b516ba7d5e290f485d3eb9672efc00f0583730179e8                          0.4s
	 => [2/2] RUN apk add --no-cache --update nmap-ncat                                                                2.4s
	 => exporting to image                                                                                             0.1s
	 => => exporting layers                                                                                            0.1s
	 => => writing image sha256:61b788982302a4f81bb71e7e5ad75b1efa3cd019603d8c333aa0ac86f7c0fed9                       0.0s
	 => => naming to docker.io/library/simple-udpserver                                                                0.0s

	Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
	
	hellbruh@PEP:/tmp/docker/simple-tcpserver/docker$ docker run -p 11211:11211 simple-udpserver
	Ncat: Version 7.92 ( https://nmap.org/ncat )
	Ncat: Listening on :::11211
	Ncat: Listening on 0.0.0.0:11211
	Ncat: Connection from 172.17.0.1.
	Ncat: Connection from 172.17.0.1:59364.
	
to detach from the server press Ctrl-P Ctrl-Q and stop server with 

	docker stop <container id>

	docker ps -a
	
will show all container images
