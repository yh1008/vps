# vps
vps on google cloud with shadowshocks

[resource](http://godjose.com/2017/06/14/new-article/)

### install ss

```  
$ sudo –i 
$ apt update
$ apt upgrade
$ sudo apt-get update  
$ sudo apt-get install python-pip  
$ sudo pip install shadowsocks  
```

### ss set up

``` 
$ sudo vim /etc/ss-conf.json 
```
copy-paste
```
{
"server":"0.0.0.0",
"server_port":8688,
"local_address":"127.0.0.1",
"locl_port":1080,
"password":"yh2901",                      
"timeout":600,
"method":"aes-256-cfb"
}
```
### start ss

``` sudo ssserver -c /etc/ss-conf.json -d start ```


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




