# Deploy vnfs with docker compose - JSON chain solution
This yaml deploy the chain

    launcher -> vnf1 -> vnf2 -> http://192.168.1.2:55634

Where:
 - `launcher` refers to [this container](https://hub.docker.com/r/augugrumi/launchervnf/) to encapsulate the message into a JSON
 - `vnf1` refers to [this container](https://hub.docker.com/r/augugrumi/addervnf/) to append a string (`vnf1` in this case) to
 the original message
 - `vnf2` refers to [this container](https://hub.docker.com/r/augugrumi/addervnf/) to append a string (`vnf2` in this case) to
 the original message
 - We suppose that on http://192.168.1.2:55634 (change with your ip address) there is a something waiting for messages
 
 ## Usage
 Download the `docker-compose.yaml` file and run `docker-compose up`. Retrieve the IP address of launcher container
 `docker ps -a | grep launcher` and then copy the CONTAINER ID. After run `docker inspect <container-id> | grep IPAddress`.
 Finally you can run `curl <launcher-ip>:55633 -X POST -d "<whatever>"`
