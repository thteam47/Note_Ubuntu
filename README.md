# Note_Ubuntu
1. Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable) [duplicate]
- For above wait for the process to complete. If this does not happen run in terminal:\
  sudo killall apt apt-get
- If none of the above works, remove the lock files. Run in terminal: \
  sudo rm /var/lib/apt/lists/lock \
  sudo rm /var/cache/apt/archives/lock \
  sudo rm /var/lib/dpkg/lock* \
- then reconfigure the packages. Run in terminal:\
  sudo dpkg --configure -a
- and\
  sudo apt update
- That should do the job.
2. Set Proxy Docker Ubuntu

step 1: sudo systemctl start docker

step 2: sudo systemctl enable docker
(Created symlink from /etc/systemd/system/multi-user.target.wants/docker.service to /usr/lib/systemd/system/docker.service.)

step 3: sudo systemctl status docker

step 4: sudo mkdir -p /etc/systemd/system/docker.service.d

step 5: sudo vi /etc/systemd/system/docker.service.d/proxy.conf

Set proxy as below
```
[Service]
Environment="HTTP_PROXY=http://proxy.server.com:80"
Environment="HTTPS_PROXY=http://proxy.server.com:80"
Environment="NO_PROXY=.proxy.server.com,*.proxy.server.com,localhost,127.0.0.1,::1"
```

step 6: 
```
sudo systemctl daemon-reload
```
step 7: 
```
sudo systemctl restart docker.service
```
step 8: 
```
vi /etc/environment and source /etc/environment
```
```
http_proxy=http://proxy.server.com:80
https_proxy=http://proxy.server.com:80
ftp_proxy=http://proxy.server.com:80
no_proxy=127.0.0.1,10.0.0.0/8,3.0.0.0/8,localhost,*.abc.com
```
