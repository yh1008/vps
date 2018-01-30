# vps
vps on google cloud with shadowshocks

[resource](http://godjose.com/2017/06/14/new-article/)

### auto restart ss

``` $ sudo vim /etc/rc.local ```


### add shadowsocks 

``` $ sudo vim /etc/init.d/shadowsocks  ```

copy-paste
```
#!/bin/sh

start(){
        ssserver -c /etc/shadowsocks.json -d start
}

stop(){
        ssserver -c /etc/shadowsocks.json -d stop
}

case "$1" in
start)
        start        
        ;;
stop)
        stop        
        ;;
reload)
        stop
        start        
        ;;
*)
        echo "Usage: $0 {start|reload|stop}"
        exit 1        
        ;;
esac
```

make it executable
```
$ sudo chmod +x /etc/init.d/shadowsocks
``` 

make new file 
```
$ sudo vim /etc/init/shadowsocks.conf
```

``` $ sudo update-rc.d shadowsocks defaults ```

``` $ sudo service shadowsocks {start|reload|stop} ```




