FROM --platform=linux/amd64 postgres:16-bullseye

LABEL maintainer="your-team"
LABEL description="PostgreSQL for Kylin V10 x86_64"

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 5432