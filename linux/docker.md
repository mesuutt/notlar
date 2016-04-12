
**[Container'in portunu hosta bind etme](http://docs.docker.io/en/latest/use/port_redirection/#binding-a-port-to-a-host-interface)**

```
-p localhost:local_port:contaner_port 
```

**Host dizinini container'a mount etme**

```
-v host_src_path:contaner_desc_path
```

**Detact tty**

```
ctrl-p + ctrl-q
```

** Get IP of container

```
docker inspect -format '{{ .NetworkSettings.IPAddress }}' $CID
```

Bu sekilde docker inspect teki herhangi bir configide alabiliriz.

Bulundugumuz dizindeki Dockerfile ile container build etme

```
docker build -t mesuutt/firefox .
```



- Volume eklerken mount edecegimiz dizinin tam yolunu vermeliyiz.

    `docker run --rm -v `pwd`/code:/code:rw -ti --name=con_blog mesuutt/blog`
- Container i baska bir user ile calistirma
    `docker run -u=0 .....`  => Container i root ile calistirir.

** Copy file from container to host
    `docker cp CONTAINER:PATH HOSTPATH`


FAQ
---
Note: If you receive the following Gtk error:
```
Gtk-WARNING **: cannot open display: unix:0.0
```
Simply allow the docker user to communicate with your X session
```
xhost +local:docker
```
