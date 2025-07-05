Docker Quick Start (Ubuntu LTS)
------------

:warning:
This Docker is barely maintained at the moment.
PRs welcome!

1. Install Docker
```bash
sudo apt update
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo usermod -aG docker $USER
# Enable Docker to start on boot
sudo systemctl enable docker
# Start Docker service
sudo systemctl start docker
# Check status
sudo systemctl status docker
```

2. Type these commands to build the Docker image:
```bash
git clone https://github.com/ail-project/ail-framework.git
cd AIL-framework
cp -r ./other_installers/docker/Dockerfile ./other_installers/docker/docker_start.sh ./other_installers/docker/pystemon ./
cp ./configs/update.cfg.sample ./configs/update.cfg
vi ./configs/update.cfg # (set auto_update to False)
docker build --build-arg tz_buildtime=Europe/Luxembourg -t ail-framework .
```

3. To start AIL on port 7000, type the following command below:
```
docker run -p 7000:7000 ail-framework
```

4. To debug the running container, type the following command and note the container name or identifier:
```bash
docker ps
```

After getting the name or identifier type the following commands:
```bash
docker exec -it CONTAINER_NAME_OR_IDENTIFIER bash
cd /opt/ail
```

Install using Ansible
---------------------

Please check the [Ansible readme](ansible/README.md).

