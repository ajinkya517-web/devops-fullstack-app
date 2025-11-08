# syntax=docker/dockerfile:1
FROM golang:1.19 AS builder

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY . .

RUN go build -o main .

# Final lightweight image
FROM alpine:latest
WORKDIR /root/

COPY --from=builder /app/main .

# Set environment variables
ENV PORT=8080

EXPOSE 8080

CMD ["./main"]