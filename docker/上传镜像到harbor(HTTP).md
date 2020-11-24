##### step 1
```
vi /etc/docker/daemon.json
```

###### step 2
```
{
"insecure-registries" : ["myregistrydomain.com:5000", "0.0.0.0"]
}
```
##### step 3 
```
systemctl restart docker
```

link: https://goharbor.io/docs/2.0.0/install-config/run-installer-script/#connect-http