FROM golang:1.21 AS build
WORKDIR /app
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 go build -o /binary

FROM gcr.io/distroless/static-debian12:latest-amd64
COPY --from=build /binary /app
EXPOSE 8080
EXPOSE 9090
CMD ["/app"]
