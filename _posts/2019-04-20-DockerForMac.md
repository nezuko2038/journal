---
layout: post
category: Docker
tags: [ Docker ]
description:
revdate:  2019-04-20  15:54 +0900
---
# MacでDockerのインストール




## インストール

HomeBrewからではなくdmgを入手しインストール
https://www.docker.com/products/docker#/mac

　

```
docker --version
Docker version 18.09.2, build 6247962
```


```
docker info
Containers: 1
 Running: 0
 Paused: 0
 Stopped: 1
Images: 13
Server Version: 18.09.2
Storage Driver: overlay2
 Backing Filesystem: extfs
 Supports d_type: true
 Native Overlay Diff: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
 Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
Swarm: inactive
Runtimes: runc
...
```
