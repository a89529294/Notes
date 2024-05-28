See folder at `/Users/admin/Desktop/courses/bootdev/docker/sample-go-web-server`

1. After creating `main.go`, run `go mod init github.com/a89529294/sample-go-web-server`
2. Run `GOOS=linux GOARCH=amd64 go build` to build a executable for linux
3. Create a `Dockerfile` in the root of the project.
4. `docker build . -t sample-go-web-server:latest`
5. `docker run -p 8080:8080 sample-go-web-server`