# ---------- Build Stage ----------
FROM golang:1.19-alpine AS build

# Set working directory
WORKDIR /app

# Copy go module files and download dependencies
COPY go.mod go.sum ./
RUN go mod download

# Copy the entire project
COPY . .

# Build the Go binary
RUN go build -o server main.go

# ---------- Run Stage ----------
FROM alpine:latest

# Set working directory for runtime
WORKDIR /app

# Copy binary from build stage
COPY --from=build /app/server .

# Expose backend port
EXPOSE 8080

# Run the backend server
CMD ["./server"]
