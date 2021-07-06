FROM golang:1.16 AS build
WORKDIR /go/src
ADD . .
ENV PATH="/go/bin:${PATH}"
RUN CGO_ENABLED=0 GOOS=linux go build -o server server.go

FROM scratch AS bin
WORKDIR /app
COPY --from=build /go/src .
EXPOSE 8000
CMD ["/app/server"]