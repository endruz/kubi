FROM python:3.7-slim-buster

WORKDIR /aria2

RUN apt update && \
    # 安装 aria2
    apt install -y aria2 && \
    # 创建目录
    mkdir config script download && \
    touch aria2.session dht.dat dht6.dat && \
    # 清理文件
    apt autoremove --purge -y && \
    apt-get clean

COPY aria2.conf /aria2/config/aria2.conf

CMD ["aria2c", "--conf-path=/aria2/config/aria2.conf"]
