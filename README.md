

## Doc

https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/

### Server
We dont create a volume inside dockers space, we use one that we create under `/usr/local/bin`.
```bash
docker run -d \
  -p 8000:8000 -p 9000:9000 \
  --name=portainer \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /usr/local/bin/portainer:/data \
  portainer/portainer-ce
```
### Agent
```bash
docker run -d \
  -p 9001:9001 \
  --name portainer_agent \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /var/lib/docker/volumes:/var/lib/docker/volumes \
  portainer/agent
```
