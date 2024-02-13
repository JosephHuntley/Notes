# Images

- Read-only file used to create containers.
- A template.
- `docker build -t <name>:<version> .` 
    - Used to build the image.
    - Ends with space dot ' .'
- `-d` is for disconnect. It disconnects the container from the terminal.
- `docker rmi` 
    - Remove a docker image
- 

# Container

- Isolated environments that share the same OS Kernel. 
- Docker containers all use the same Kernel and the containers only contain differences. 
- ` docker attach <name>` to reattach the terminal to a container
-  `docker run --name <containerName> -p <computerPort>:<containerPort> <imageName>`
    - Used to run a container for the first time.
- `docker rm`
    - Remove a container
- You can map folders similar to ports with the -v flag.
- `-e` is for environmental variables. 