FROM golang:1.15 as builder

RUN go get github.com/codegangsta/negroni
RUN go get github.com/gorilla/mux
RUN go get github.com/xyproto/simpleredis/v2

COPY main.go .

RUN go build -o /go/main main.go

FROM ubuntu:18.04

COPY --from=builder /go/main /app/guestbook

COPY public/index.html /app/public/index.html
COPY public/script.js /app/public/script.js
COPY public/style.css /app/public/style.css
COPY public/jquery.min.js /app/public/jquery.min.js

WORKDIR /app

CMD ["./guestbook"]

EXPOSE 3000
