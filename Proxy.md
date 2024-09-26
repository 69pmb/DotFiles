---
title: Proxy settings
---  
#### Sets proxy for unix systems  

```bash
export http_proxy=proxy.fr:3128
export https_proxy=$http_proxy
export no_proxy=localhost,127.0.0.1,pmb-VirtualBox,$http_proxy,.local
export NO_PROXY=$no_proxy
```

#### Add proxy in /etc/hosts file

`<ip-address>  proxy.fr`

#### Remove  

```bash
unset http_proxy
unset http_proxy
unset no_proxy
unset NO_PROXY
```

#### Spring boot

`-Dhttp.proxyHost=proxy.fr -Dhttp.proxyPort=3128 -Dhttps.proxyHost=proxy.fr -Dhttps.proxyPort=3128 -Dhttps.proxySet=true`

#### Apt-get

```bash
/etc/apt/apt.conf.d/01proxy
/etc/apt/apt.conf
Acquire::http::Proxy "http://proxy.fr:3128";
```

#### Docker

```bash
/etc/systemd/system/docker.service.d/http-proxy.conf
[Service]
Environment="http_proxy=http://proxy.fr:3128"
Environment="https_proxy=http://proxy.fr:3128"
Environment="no_proxy=localhost,127.0.0.1,.proxy.fr,.local"
sudo systemctl daemon-reload
sudo systemctl show --property Environment docker
sudo systemctl restart docker
```
