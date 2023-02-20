FROM golang:1.19.6-alpine3.17

RUN apk update && apk upgrade && apk add --no-cache bash git

WORKDIR /app

COPY go.mod ./
COPY go.sum ./

RUN go mod download

COPY client/*.go ./

RUN go build -o /client-discovery

ENV SOURCES /Users/rafli/GolandProjects/demo-go-discovery-services/
COPY . ${SOURCES}

RUN cd ${SOURCES}client/ && CGO_ENABLED=0 go build

ENV CONSUL_HTTP_ADDR localhost:8500

WORKDIR ${SOURCES}client/
CMD ${SOURCES}client/client