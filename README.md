# gomockhandler

gomockhandler handler of [golang/mock](https://github.com/golang/mock), as the name implies.

People usually create mock with `go generate`. 
But, `go generate` is not fast. And we cannot easily check if mock is up-to-date.

- You can generate mocks more **quickly** :rocket:. Your mock will be generated in parallel.
- You can check if mock is up-to-date :sparkles:.
- You can manage your mocks in one config file :books:.
- You can generate the config of gomockhandler **just by rewriting `go:generate` comment** a little bit :wrench:.

## Install

You have to install `mockgen` first.

### Go version < 1.16
```
GO111MODULE=on go get github.com/golang/mock/mockgen
GO111MODULE=on go get github.com/sanposhiho/gomockhandler
```
### Go 1.16+
```
go install github.com/golang/mock/mockgen
go install github.com/sanposhiho/gomockhandler
```

## How to use

### [preparation] generate config file by rewriting `go:generate` comment

replace from `mockgen` to `gomockhandler -project_root=/path/to/project_root`, and run `go generate ./...` in your project.

```
- //go:generate mockgen -source=$GOFILE -destination=mock_$GOFILE -package=$GOPACKAG
+ //go:generate gomockhandler -project_root=/path/to/project -source=$GOFILE -destination=mock_$GOFILE -package=$GOPACKAG
```

gomockhandler generate `gomockhandler.json` in your project root directory.

### generate mock

```
gomockhandler -config=gomockhandler.json -concurrency=100 mockgen
```

### check your mock is up-to-date

```
gomockhandler -config=gomockhandler.json check
```

You can see the error if some mocks are not up to date.

```
2021/03/06 02:37:16 mock is not up to date. source: user.go, destination: ../mock/user.go
```

## How to manage your mocks

### Add a new mock to be generated

You can use the same options as mockgen to add a new mock to be generated.
`mockgen` has two modes of operation: source and reflect, and, gomockhandler support both.

See [golang/mock#running-mockgen](https://github.com/golang/mock#running-mockgen) for more information.


Example(Source mode):
```
gomockhandler -source=foo.go [other options]
```

Example(Reflect mode):
```
gomockhandler [options] database/sql/driver Conn,Driver
```
