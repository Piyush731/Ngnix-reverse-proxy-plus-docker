FROM golang:1.22.3-alpine
RUN apk add --no-cache curl
WORKDIR /app
COPY . .
RUN go build -o service1
EXPOSE 8001
HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
  CMD curl -f http://localhost:8001/ping || exit 1
CMD ["./service1"]