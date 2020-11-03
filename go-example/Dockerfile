# Start by building the application.
FROM distroless.jfrog.io/docker/golang:1.13-buster as build

WORKDIR /go/src/app
ADD . /go/src/app

RUN go get -d -v ./...

RUN go build -o /go/bin/app

# Now copy it into our base image.
FROM distroless.jfrog.io/docker/distroless/base-debian10
COPY --from=build /go/bin/app /
CMD ["/app"]
