## Android

## Docker

Docker Engine Daemon

### macOS

Docker Desktop -> Preferences -> Docker Engine

change content to:

    {
      "experimental": false,
      "debug": true,
      "registry-mirrors": [
        "http://f1361db2.m.daocloud.io",
        "https://docker.mirrors.ustc.edu.cn/",
        "https://hub-mirror.c.163.com",
        "https://registry.docker-cn.com"
      ]
    }

**WARNING** All the running container will be stopped

Click `Apply & Restart`

## GNU/Linux

`sudo vim /etc/docker/daemon.json`

**WARNING** All the running container will be stopped

`sudo service docker restart`

## Flutter

## Homebrew

## Golang

## NodeJS
    # When in China, set $NODEJS_ORG_MIRROR
    export NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node/
