# 基于官方镜像，指定 linux/amd64 平台
FROM --platform=linux/amd64 postgres:16-bullseye

# 元信息
LABEL maintainer="your-team"
LABEL description="PostgreSQL for Kylin V10 x86_64"

# 安装额外工具（按需）
RUN apt-get update && apt-get install -y --no-install-recommends \
    postgresql-16-pg-jieba \   # 中文分词插件（按需）
    curl \
    && rm -rf /var/lib/apt/lists/*

# 拷贝自定义配置（可选）
# COPY conf/postgresql.conf /etc/postgresql/postgresql.conf

# 拷贝初始化脚本（容器首次启动时自动执行）
COPY initdb/ /docker-entrypoint-initdb.d/

# 设置时区为中国标准时间
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 5432