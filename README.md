# Yet another SIP003 plugin for shadowsocks, based on GOST Tunnel

## Build

* `go build`

## Usage

See command line args for advanced usages.

### Shadowsocks over TLS/Multiplex TLS

On your server

```sh
ss-server -c config.json -p 443 --plugin gost-plugin --plugin-opts "server;cert=cert.pem;key=key.pem;mode=tls"
ss-server -c config.json -p 443 --plugin gost-plugin --plugin-opts "server;cert=cert.pem;key=key.pem;mode=mtls"
```

On your client

```sh
ss-local -c config.json -p 443 --plugin gost-plugin --plugin-opts "serverName=mydomain.me;mode=tls"
ss-local -c config.json -p 443 --plugin gost-plugin --plugin-opts "serverName=mydomain.me;mode=mtls;mux=1"
```

### Shadowsocks over Websocket/Multiplex Websocket (HTTP)

On your server

```sh
ss-server -c config.json -p 80 --plugin gost-plugin --plugin-opts "server;mode=ws"
ss-server -c config.json -p 80 --plugin gost-plugin --plugin-opts "server;mode=mws"
```

On your client

```sh
ss-local -c config.json -p 80 --plugin gost-plugin --plugin-opts "mode=ws"
ss-local -c config.json -p 80 --plugin gost-plugin --plugin-opts "mode=mws;mux=1"
```

### Shadowsocks over Http2/Websocket/Multiplex Websocket (HTTPS)

On your server

```sh
ss-server -c config.json -p 443 --plugin gost-plugin --plugin-opts "server;cert=cert.pem;key=key.pem;mode=h2"
ss-server -c config.json -p 443 --plugin gost-plugin --plugin-opts "server;cert=cert.pem;key=key.pem;mode=wss"
ss-server -c config.json -p 443 --plugin gost-plugin --plugin-opts "server;cert=cert.pem;key=key.pem;mode=mwss"
```

On your client

```sh
ss-local -c config.json -p 443 --plugin gost-plugin --plugin-opts "serverName=mydomain.me;mode=h2"
ss-local -c config.json -p 443 --plugin gost-plugin --plugin-opts "serverName=mydomain.me;mode=wss"
ss-local -c config.json -p 443 --plugin gost-plugin --plugin-opts "serverName=mydomain.me;mode=mwss;mux=1"
```

### Shadowsocks over QUIC

On your server

```sh
ss-server -c config.json -p 443 --plugin gost-plugin --plugin-opts "server;cert=cert.pem;key=key.pem;mode=quic"
```

On your client

```sh
ss-local -c config.json -p 443 --plugin gost-plugin --plugin-opts "serverName=mydomain.me;mode=quic"
```

### Shadowsocks over gRPC(Experiment)

On your server

```sh
ss-server -c config.json -p 443 --plugin gost-plugin --plugin-opts "server;cert=cert.pem;key=key.pem;mode=grpc"
```

On your client

```sh
ss-local -c config.json -p 443 --plugin gost-plugin --plugin-opts "serverName=mydomain.me;mode=grpc"
```
