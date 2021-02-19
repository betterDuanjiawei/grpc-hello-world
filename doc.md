## Grpc-gateway
* 是什么
    grpc-gateway是protoc的一个插件。它读取gRPC服务定义，并生成一个反向代理服务器，将RESTful JSON API转换为gRPC。此服务器是根据gRPC定义中的自定义选项生成的。
* 安装
    go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grp
    
## 报错
* 
```
go run client.go
2021/02/19 15:05:15 rpc error: code = Unavailable desc = connection error: desc = "transport: authentication handshake failed: x509: certificate is valid for grpc-hello-world, not dev"
panic: runtime error: invalid memory address or nil pointer dereference
[signal SIGSEGV: segmentation violation code=0x1 addr=0x28 pc=0x14886d9]

goroutine 1 [running]:
main.main()
        /Users/v_duanjiawei/go/src/github.com/betterDuanjiawei/grpc-hello-world/client/client.go:36 +0x339
creds, err := credentials.NewClientTLSFromFile("../certs/server.pem", "dev")
这里写的服务名称和生成证书时候不一致

2021/02/19 15:30:22 rpc error: code = Unavailable desc = connection error: desc = "transport: authentication handshake failed: x509: certificate relies on legacy Common Name field, use SANs or temporarily enable Common Name matching with GODEBUG=x509ignoreCN=0"
panic: runtime error: invalid memory address or nil pointer dereference
[signal SIGSEGV: segmentation violation code=0x1 addr=0x28 pc=0x14886d9]

goroutine 1 [running]:
main.main()
        /Users/v_duanjiawei/go/src/github.com/betterDuanjiawei/grpc-hello-world/client/client.go:36 +0x339
exit status 2

 GODEBUG=x509ignoreCN=0 go run client.go
```

```
go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-swagger
sudo cp /Users/v_duanjiawei/go/bin/protoc-gen-swagger /usr/local/go/bin/
protoc -I/usr/local/include -I. -I$GOPATH/src/github.com/betterDuanjiawei/grpc-hello-world/proto/google/api --swagger_out=logtostderr=true:. ./hello.proto

安装go-bindata
go get -u github.com/jteeuwen/go-bindata/...
 sudo cp /Users/v_duanjiawei/go/bin/go-bindata /usr/local/go/bin/
```

## goland the file size exceeds configured limit
* [IDEA加载大文件时报错:The file size exceeds configured limit](https://blog.csdn.net/qq_34321590/article/details/106131393)