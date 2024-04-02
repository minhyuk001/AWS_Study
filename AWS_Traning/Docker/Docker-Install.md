```
sudo yum install docker -y
sudo usermod -aG docker <AMI Name>
sudo systemctl enable --now docker
sudo chmod 666 /var/run/docker.sock
```
