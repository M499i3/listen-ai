FROM golang:1.24-alpine AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . ./
RUN CGO_ENABLED=0 GOOS=linux go build -o /usr/local/bin/stat-service .

FROM alpine:3.22

WORKDIR /app

ENV STAT_PORT=8002 \
    SQLITE_PATH=/data/listenai.db

COPY --from=builder /usr/local/bin/stat-service /usr/local/bin/stat-service

EXPOSE 8002

CMD ["stat-service"]
