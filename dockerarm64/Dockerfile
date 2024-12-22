FROM ubuntu:latest

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="Local version:- ${VERSION} Build-date:- ${BUILD_DATE}"
LABEL maintainer="myhme"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update && \
    apt-get -y upgrade && \
	apt install -y wget curl && \
	t=$(mktemp) && \
	wget 'https://dist.1-2.dev/imei.sh' -qO "$t" && \
	bash "$t" && \
	rm "$t" && \
	curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.4.6/powershell-7.4.6-linux-arm64.tar.gz && \
	mkdir -p /opt/microsoft/powershell/7 && \
        tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7 && \
	chmod +x /opt/microsoft/powershell/7/pwsh && \
	ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh && \
	rm -rf /tmp/*

WORKDIR /app
COPY . /app

ENTRYPOINT ["sleep","infinity"]
