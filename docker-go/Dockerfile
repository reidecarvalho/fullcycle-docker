FROM golang AS builder
WORKDIR /usr/src/app
COPY hello-world.go .
RUN go build hello-world.go

# Final
FROM scratch
WORKDIR /app
COPY --from=builder /usr/src/app/hello-world .
ENTRYPOINT ["./hello-world"]