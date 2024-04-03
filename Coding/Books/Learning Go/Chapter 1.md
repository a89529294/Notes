The first thing you need is create a directory to hold your program
- `mkdir ch1` `cd ch1`
- `go mod init hello_world`
A _Go project_ is called a _module_.

Every module has a go.mod file in its root directory. Running `go mod init` creates this file for you.

The _go.mod_ file declares the name of the module, the minimum supported version of Go for the module, and any other modules that your module depends on.

Within a _Go module_, code is organized into _one or more packages_. The _main package_ in a Go module contains the code that _starts a Go program_.

All Go programs __start__ from the _main function in the main package_.

- `touch hello.go`, add some code to print out "Hello, world!"
- `go build` this will build a binary with name `hello_world`, which is the module name. Use `go build -o new_name` to give it a new name or output the binary somewhere else.
- `./hello_world` to run the binary
- `go vet` to detect some errors

### go playground
https://go.dev/play/
- use `-- filename.go --` to simulate different files
- use `--subdir/my_code.go --` to simulate subdirectories

## make file
A set of operations that are necessary to build a program and the order in which the steps must be performed.
- `touch Makefile`
- paste in 
```
.DEFAULT_GOAL := build

.PHONY:fmt vet build
fmt:
	go fmt ./...

vet: fmt
	go vet ./...

build: vet
	go build
```
- `make` 

