FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
ENV CGO_ENABLED=0
RUN go build -o hello .

# Docker 제공 경량 이미지
FROM scratch
# --from=${stage_name} 로 지정한 스테이지 결과물을 해당 스테이지에 복사
COPY --from=builder /app/hello /hello
ENTRYPOINT ["/hello"]