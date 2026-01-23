# Tools

## Install

### curl

```bash
sudo apt-get install -y curl
```

```bash
brew install curl
```


### grpc_curl

```bash
go install github.com/fullstorydev/grpcurl/cmd/grpcurl@latest
```

```bash
ln -s "$(go env GOPATH)/bin/grpcurl" "$(go env GOPATH)/bin/grpc_curl"
```

### grpc

```bash
brew install grpc
```

```bash
ln -s "$(brew --prefix)/bin/grpc_cli" /usr/local/bin/grpc
```

## Use

### curl

```bash
curl -X GET http://localhost:8080/health
```

```bash
curl -X POST http://localhost:8080/apx/characters \
  -H "Content-Type: application/json" \
  -d '{"table":"characters","filters":{"name":"ana"}}'
```


### grpc_curl

```bash
grpc_curl -plaintext localhost:50051 list
```

```bash
grpc_curl -plaintext localhost:50051 describe service.service
```

```bash
grpc_curl -plaintext localhost:50051 \
  -d '{"table":"characters","id":"1"}' \
  service.service/Read
```

### grpc

```bash
grpc ls localhost:50051
```

```bash
grpc call localhost:50051 service.service/Read \
  '{"table":"characters","id":"1"}'
```
