FROM golang:1.10 as builder
RUN go get github.com/codegangsta/negroni
RUN go get github.com/gorilla/mux github.com/xyproto/simpleredis
COPY main.go .
RUN go build main.go

FROM ubuntu:20.04

WORKDIR /app
COPY --from=builder /go/main guestbook
COPY public public

EXPOSE 8080
CMD ["./guestbook"]
