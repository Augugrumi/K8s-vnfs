# Deploy vnfs on kubernetes with multiple pods - JSON chain solution
This yaml deploy the chain

    launcher -> vnf1 -> vnf2 -> http://192.168.30.13:55634

Where:
 - `launcher` refers to [this container](https://hub.docker.com/r/augugrumi/launchervnf/) to encapsulate the message into a JSON
 - `vnf1` refers to [this container](https://hub.docker.com/r/augugrumi/addervnf/) to append a string (`vnf1` in this case) to
 the original message
 - `vnf2` refers to [this container](https://hub.docker.com/r/augugrumi/addervnf/) to append a string (`vnf2` in this case) to
 the original message
 - We suppose that on http://192.168.30.13:55634 (change with your ip address) there is a something waiting for messages
 
## Usage
Download the `unique-pod.yaml` file and run `kubectl apply -f unique-pod.yaml`. This will create a service and a pod for each
container.
