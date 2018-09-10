#
# BUILD 阶段
# 
FROM golang:1.10 AS build

# 设置我们应用程序的工作目录
WORKDIR /go/src/github.com/scboffspring/blog-multistage-go

# 添加所有需要编译的应用代码
ADD . .

# 编译一个静态的go应用（在二进制构建中包含C语言依赖库）
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo .

# 设置我们应用程序的启动命令
CMD ["./blog-multistage-go"]


# 
# CERTS Stage
#
FROM alpine:latest as certs

# Install the CA certificates
RUN apk --update add ca-certificates

#
# PRODUCTION STAGE
# 
FROM scratch AS prod

# 从certs阶段拷贝CA证书
COPY --from=certs /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
# 从buil阶段拷贝二进制文件
COPY --from=build /go/src/github.com/scboffspring/blog-multistage-go/blog-multistage-go .
CMD ["./blog-multistage-go"]
