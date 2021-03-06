### Tuna - a tunnel program

`Tuna` is a network tunneling software working as an encryption wrapper between clients and servers (remote/local).

`Tuna` is forked from [qTunnel](https://github.com/getqujing/qtunnel).

##### Why Tuna

- Support loading parameters from config file
- Web server
- UI

### Requirements

[golang 1.9](http://golang.org/dl/)

### Build

To build `tuna`

```
$ make
```

To test `tuna`

```
$ make test
```

### Usage

```
$ tuna
```

### Configure

The topology is:
```
app <------> tuna (client) <------> tuna (server) <------> service
```

On `client`:
```
{
  "ClientMode": true,
  "ListenAddr": ":9527",
  "Secret": "This is a secret",
  "Crypto": "aes256cfb",
  "Backends": [
    {
      "Name": "be1",
      "Addr": "192.168.1.100:443",
      "Using": true
    }
  ]
}
```

On `server`:
```
{
  "ClientMode": false,
  "ListenAddr": ":443",
  "Secret": "This is a secret",
  "Crypto": "aes256cfb",
  "Backends": [
    {
      "Addr": ":3128",
      "Using": true
    }
  ]
}
```

Both servers and clients should use the same `crypto` and same `secret`.

Please note the config file should be named as `config.json`, and placed in the same folder of the exec folder. And comments are not supported as it is a json file.



