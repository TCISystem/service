FROM golang:1.10.0

WORKDIR /go/src/github.com/TCISystem/service
COPY . .
RUN go get -d -v github.com/TCISystem/service/apiserver && \
    CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o /app ./apiserver

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=0 /app .
CMD ['./app']
