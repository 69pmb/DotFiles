Sets proxy for unix systems:  

```bash
export http_proxy=proxy.fr:3128
export https_proxy=$http_proxy
export no_proxy=localhost,127.0.0.1,devbox,$http_proxy,.local
export NO_PROXY=$no_proxy
```