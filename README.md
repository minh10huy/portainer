# portainer

docker service create \
    --name portainer \
    --publish 10001:9000 \
    --constraint 'node.role == manager' \
    --mount type=bind,src=/home/pirate/docker/portainer,dst=/data \
     --mount type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock \
    portainer/portainer \
    -H unix:///var/run/docker.sock
    
docker run -d -p 10001:9000 --name=portainer \
  -v "/var/run/docker.sock:/var/run/docker.sock" \
  -v /home/pirate/docker/portainer:/data \
  portainer/portainer
