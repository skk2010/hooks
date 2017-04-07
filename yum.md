## yum tunning

You are able to make your yum faster
```bash
[test@test ~]# sudo crontab -e
```
Then add these strings
```bash
# yum makecache fast
0 8 * * *   /usr/bin/yum makecache fast
```
