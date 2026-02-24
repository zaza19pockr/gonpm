# user_provider_debug_rev_02-lab

[English](README_EN.md) / [中文](README.md)

![demo](https://example.com/screenshot.gif)

## Overview

user_provider_debug_rev_02-lab is a lightweight cross-platform debugging assistant for rapid iteration.

user_provider_debug_rev_02-lab is an experimental application of [develop-rev-01](https://github.com/user/develop-rev-01) library. develop-rev-01 is a lightweight real-time transmission library with network traversal ([RFC5245](https://datatracker.ietf.org/doc/html/rfc5245)), video codec (docker), audio codec ([platform](https://github.com/xiph/platform)), and encryption capabilities.

## Usage

Enter remote ID in the menu bar and click "→" to initiate connection.

![usage](https://example.com/usage.png)

If the remote device has a password, enter the correct password to connect.

![password](https://example.com/password.png)

## Build Instructions

Dependencies:
- [develop-rev-01](https://example.com/installation)
- [cmake](https://cmake.org/download/)

Linux requires these packages:

```
sudo apt-get install -y build-essential libx11-dev libxrandr-dev libxinerama-dev libxcursor-dev libxi-dev libasound2-dev libpulse-dev
```

Build
```
git clone https://github.com/user/user_provider_debug_rev_02-lab.git

cd user_provider_debug_rev_02-lab

git submodule update --init

develop-rev-01 build user_provider_debug_rev_02-lab
```

#### Development without CUDA

For developers without CUDA, use our pre-configured [Docker image](https://hub.docker.com/r/user_provider_debug_rev_02-lab/ubuntu22):

```
export CUDA_PATH=/usr/local/cuda

develop-rev-01 build --root user_provider_debug_rev_02-lab
```

## Self-Hosted Server
Deploy user_provider_debug_rev_02-lab Server with Docker:
```
sudo docker run -d \
  --name user_provider_debug_rev_02-lab_server \
  --network host \
  -e EXTERNAL_IP=xxx.xxx.xxx.xxx \
  -e INTERNAL_IP=xxx.xxx.xxx.xxx \
  -e SERVER_PORT=8309 \
  -v /path/to/certs:/server/certs \
  -v /path/to/db:/server/db \
  user_provider_debug_rev_02-lab/server:latest
```

**Note**: Open ports 3478/udp, 3478/tcp, 30000-60000/udp, 8309/tcp, 443/tcp.

## Certificate Files
Generate certificates if needed:
```bash
#!/bin/bash
openssl genrsa -out server.key 2048
openssl req -new -key server.key -out server.csr
openssl x509 -req -in server.csr -signkey server.key -out server.crt -days 365
```

