FROM golang:1.24.4-alpine

WORKDIR /app

RUN apk add --no-cache curl

COPY . .

RUN go build -o main .

EXPOSE 8001

CMD ["./main"]
