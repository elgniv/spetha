# SPETHA

forked from [jphastings/hadiscover](https://github.com/jphastings/hadiscover)

[specialone](https://github.com/elgniv/specialone) + [etcd](https://github.com/coreos/etcda) + [HAProxy](http://www.haproxy.org/)

## Usage

```
# replace `<YOUR_ETCD_HOST>` to yours

## run specialone for service discovery
$ sudo docker run -d --net=host -v /var/run/docker.sock:/var/run/docker.sock -e SP_ETCD_HOST=<YOUR_ETCD_HOST>:4001 elgniv/specialone

## run your webserver container (ex: luisbebop/docker-sinatra-hello-world) as SP_GROUP webserver
$ sudo docker run -d -e SP_GROUP=webserver -P luisbebop/docker-sinatra-hello-world

## run spetha
$ sudo docker run -p 80:80 --rm -e HADISCOVER_ETCD="http://<YOUR_ETCD_HOST>:4001" --link etcd:etcd -t elgniv/spetha
```

## Architecture

![image](https://s3.amazonaws.com/vingle-images/some/spetha.png)
