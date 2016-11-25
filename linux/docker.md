
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

Host ile container arasinda dosya transferi

```
docker cp foo.txt mycontainer:/foo.txt
docker cp mycontainer:/foo.txt foo.txt

```


- Volume eklerken mount edecegimiz dizinin tam yolunu vermeliyiz.

    `docker run --rm -v `pwd`/code:/code:rw -ti --name=con_blog mesuutt/blog`

---
### X sunucusu erisimi

Docker container icinde calisan bir uygulamanin X sunucusu ile baglanti kurabilmesi icin 2 yontem var.
Birinci ve *en tehlikeli* yonten acccess control listeleri.

```
xhost +local:docker
xhost + # Bu en tehlikelisi. X sunucumuz artik butun baglantilari kabul eder.
```


Bir digeri ise Xauth ile cookie based auth. Bu daha guvenli.
Zaten varolan Xauthority dosyamizi container a mount ederek
containerin X sunucumuza baglanti kurabilmesine izin verebiliriz.

```
-v ~/.Xauthority:/.Xauthority:ro
-e XAUTHORITY=/.Xauthority
```

http://www.tldp.org/HOWTO/Remote-X-Apps-6.html

---
