FROM golang:1.19-buster AS build

WORKDIR /app

COPY go.mod ./
COPY go.sum ./
RUN go mod download && \
    go build -o /calculator

FROM gcr.io/distroless/base-debian10

WORKDIR /

COPY --from=build /calculator /calculator

USER nonroot:nonroot

LABEL version="1.0"

ENTRYPOINT ["/calculator"]
