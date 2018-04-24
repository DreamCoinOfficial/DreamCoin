### Setup docker on Debian 8.1

Install notes: https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository

Docker CLI: https://docs.docker.com/engine/reference/run/

Script that installs docker-ce: `setup_docker_debian.sh`

### Build&Run DREM docker container

Pre: `DreamPay.conf MUST be available under link DREM_CONF_URL as pointed out in the Dockerfile`

Build container: `sudo docker build --tag drem:1.0.3 .`

Run container: `docker run -d --name drem.cont drem:1.0.3`

See if it is up: `docker ps -a`

Shell in the container: `docker exec -it drem.cont /bin/bash`

Test RPC: `drem-cli -rpcuser=drem -rpcpassword=<from config file> help`

Stop container: `docker stop drem.cont`

Delete container: `docker rm drem.cont`