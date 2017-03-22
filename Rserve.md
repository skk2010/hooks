## Installation Rserve on CentOS 7

I suppose you are using x84_64 platform
```bash
yum install R 
```
Run R
```bash
R 
```
install Rserve module
```bash
R > install.packages("Rserve",dest="/usr/lib64/R/library") 
```
Check that Rserve has been installed properly and could started
```bash
R > library("Rserve")
Rserve()
```
If Rserve started properly:
* Create conf file as /etc/Rserve.conf
[Rserve.conf](https://github.com/skk2010/hooks/blob/master/Rserve/Rserve.conf)
* Create service file to enable this service in start OS. Create file as /usr/lib/systemd/system/rserve.service
[rserve.service](https://github.com/skk2010/hooks/blob/master/Rserve/Rserve.conf)

Enable Rserve service
```bash
systemctl enable rserve
```

Looks like that's all
