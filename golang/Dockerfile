FROM golang:alpine as builder

LABEL maintainer="Magno Matos magnomatos822@gmail.com"

WORKDIR $GOPATH/src/app

COPY src/greeting/ .

RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o /go/bin/app .

FROM scratch

COPY --from=builder /go/bin/app /go/bin/app

ENTRYPOINT ["/go/bin/app"]

EXPOSE 8000