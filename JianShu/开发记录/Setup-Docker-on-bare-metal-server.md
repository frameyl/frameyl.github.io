1. Install Ubuntu
2. Install sshd by the following command
> sudo apt-get install openssh-client openssh-server
3. Login the server remotely, and install docker
> sudo apt-get install docker.io
4. In China, you will need to setup your docker image accelerator
``` bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://y2wog5ns.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```
5. Setup the user who can run docker instead of by sudo
``` bash
sudo usermod -aG docker ${USER}
su - ${USER}
```
