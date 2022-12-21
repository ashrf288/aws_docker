##

+ if you get this error :

Couldn't connect to Docker daemon at http+docker://localhost - is it running?

then run 

```
sudo usermod -aG docker $USER
sudo chown $USER /var/run/docker.sock
```