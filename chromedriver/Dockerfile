FROM python:3.7-slim-buster

ARG CHROME_DL_URL=https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
ARG CHROMEDRIVER_BASE_URL=https://chromedriver.storage.googleapis.com
ARG CHROMEDRIVER_VERSION_URL=$CHROMEDRIVER_BASE_URL/LATEST_RELEASE

RUN apt update && \
    apt install -y wget curl unzip && \
    # 安装 chrome
    wget "$CHROME_DL_URL" && \
    apt install --no-install-recommends --no-install-suggests -y ./google-chrome-stable_current_amd64.deb && \
    # 安装 chromedriver
    VERSION=$(curl -sL "$CHROMEDRIVER_VERSION_URL") && \
    wget "$CHROMEDRIVER_BASE_URL/$VERSION/chromedriver_linux64.zip" && \
    unzip chromedriver_linux64.zip && \
    chmod 755 chromedriver && \
    mv chromedriver /usr/local/bin/  && \
    # 安装 selenium
    pip install selenium  && \
    # 清理文件
    rm -f google-chrome-stable_current_amd64.deb chromedriver_linux64.zip && \
    apt autoremove --purge -y && \
    apt-get clean
