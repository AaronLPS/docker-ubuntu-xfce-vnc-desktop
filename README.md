ros-vnc
=========================
## Futures
- VNC server
- SSH

## Pull from dockerhub

```
$ docker pull paopaorobot/ros-vnc
```

## Run

### Use it headless
```
$ docker run -it paopaorobot/ros-vnc
```
Now you can use the command line

### Use it with ssh
```
$ docker run -it -p [port]:22 paopaorobot/ros-vnc
```
You will see the random password in terminal. You can use it to login ssh by
```
$ ssh -o 'UserKnownHostsFile=/dev/null' root@localhost -p [port]
```
If you want to set password by yourself, you can run 
```
$ docker run -it -p [port]:22 -e SSHPW=[YOUR_PW] paopaorobot/ros-vnc
```

You need to set the port, e.g. `2222`. 

### Use it with vnc
```
$ docker run -i -t -p 5900:5900 paopaorobot/ros-vnc
```
if you want to set resolution
```
$ docker run -i -t -p 5900:5900 -e RESOLUTION=1920x1080 paopaorobot/ros-vnc
```

Then open vnc viewer and input `<YOUR IP>:5900`, and you can use the desktop by vnc. If you run the image on your own pc, you can only input `:5900` in vnc viewer.

### Use random port
If you don't want to set port by yourself, you can use random port with `-P` param. e.g.
```
$ docker run -it -P paopaorobot/ros-vnc
```
Now, you need `docker port` to find out the ports
```
$ docker port [container_id] [port]
```
When [port] is `22`, you get the port for ssh. When [port] is `5900`, you get the port for vnc viewer.

## Trobleshooting
You can find logs under /var/log/ in container.

