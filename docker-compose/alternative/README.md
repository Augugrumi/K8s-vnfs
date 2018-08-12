# Deploy vnfs with docker compose - alternative solution
This yaml deploy the chain

    launcher -> dispatcher -> vnf1 -> vnf2 -> http://192.168.1.6:55634

Where:
 - `launcher` refers to [https://hub.docker.com/r/augugrumi/alternative-launchervnf/](this container) to encapsulate the message
 into a JSON
 - `dispatcher` refers to [https://hub.docker.com/r/augugrumi/alternative-dispatcher/](this container) to send messages to the
 vnfs to be modified
 - `vnf1` refers to [https://hub.docker.com/r/augugrumi/alternative-addervnf/](this container) to append a string (`vnf1` in
 this case) to the original message
 - `vnf2` refers to [https://hub.docker.com/r/augugrumi/alternative-addervnf/](this container) to append a string (`vnf2` in
 this case) to the original message
 - We suppose that on http://192.168.1.6:55634 (change with your ip address) there is a something waiting for messages
 
 ## Usage
 Download the `docker-compose.yaml` file and run `docker-compose up`. Retrieve the IP address of launcher container
 `docker ps -a | grep launcher` and then copy the CONTAINER ID. After run `docker inspect <container-id> | grep IPAddress`.
 Finally you can run `curl <launcher-ip>:55633 -X POST -d "<whatever>"`
