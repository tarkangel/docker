### How to install docker in Ubuntu 20.0.4 for Windows 10

##### Update ubuntu

We update ubuntu runnin the next commands:
```
~$ sudo apt-get update; sudo apt-get upgrade
```
```
~$ sudo apt install docker.io
```
Then we verify the docker installation : 
```
~$ docker --version
```
 Install Python 3 and PIP.
```
sudo apt-get install -y python3 python3-pip
```
You can copy / paste all of the commands below into your WSL terminal.

Ubuntu 18.04 / 20.04 installation notes taken from Docker’s documentation:
```
# Update the apt package list.
sudo apt-get update -y

# Install Docker's package dependencies.
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

# Download and add Docker's official public PGP key.
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Verify the fingerprint.
sudo apt-key fingerprint 0EBFCD88

# Add the `stable` channel's Docker upstream repository.
#
# If you want to live on the edge, you can change "stable" below to "test" or
# "nightly". I highly recommend sticking with stable!
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

# Update the apt package list (for the new apt repo).
sudo apt-get update -y

# Install the latest version of Docker CE.
sudo apt-get install -y docker-ce

# Allow your user to access the Docker CLI without needing root access.
sudo usermod -aG docker $USER
```
 Install Docker Compose into your user's home directory.
 ```
pip3 install --user docker-compose
```
#### Download Docker for Windows and click active on expose daemon on tcp

![image](https://user-images.githubusercontent.com/83728906/182758546-2cfc9116-3996-4bb9-83a3-df052019f72f.png)

Configure WSL to Connect to Docker for Windows
#### The next step is to configure WSL so that it knows how to connect to the remote Docker daemon running in Docker for Windows (remember, it’s listening on port 2375).


we need to add your current user to the ‘docker’ group so that you are allowed to interface with the Docker Engine which will be running on your system as root.
```
sudo usermod -aG docker $USER
```


Configure Docker to start on boot

Most current Linux distributions (RHEL, CentOS, Fedora, Debian, Ubuntu 16.04 and higher) use systemd to manage which services start when the system boots. On Debian and Ubuntu, the Docker service is configured to start on boot by default. To automatically start Docker and Containerd on boot for other distros, use the commands below:
```
 sudo systemctl enable docker.service
 sudo systemctl enable containerd.service
 ```
To disable this behavior, use disable instead.
```
 sudo systemctl disable docker.service
 sudo systemctl disable containerd.service
```


We run our firstr container:
```
~$ docker run hello-world 
```

![image](https://user-images.githubusercontent.com/83728906/182758880-66f814d4-ac81-43e1-8a61-392a17ad4a57.png)

