
```
# 添加http/https代理, apt代理, git代理
export hostip=$(ip route | grep default | awk '{print $3}')
export hostport=10809
alias proxy='
    export https_proxy="http://${hostip}:${hostport}";
    export http_proxy="http://${hostip}:${hostport}";
    export all_proxy="http://${hostip}:${hostport}";
    git config --global http.proxy "http://${hostip}:${hostport}"
    git config --global https.proxy "http://${hostip}:${hostport}"
    echo -e "Acquire::http::Proxy \"http://${hostip}:${hostport}\";" | sudo tee -a /etc/apt/apt.conf.d/proxy.conf > /dev/null;
    echo -e "Acquire::https::Proxy \"http://${hostip}:${hostport}\";" | sudo tee -a /etc/apt/apt.conf.d/proxy.conf > /dev/null;
'
alias unproxy='
    unset https_proxy;
    unset http_proxy;
    unset all_proxy;
    git config --global --unset http.proxy
    git config --global --unset https.proxy
    sudo sed -i -e '/Acquire::http::Proxy/d' /etc/apt/apt.conf.d/proxy.conf;
    sudo sed -i -e '/Acquire::https::Proxy/d' /etc/apt/apt.conf.d/proxy.conf;
'
```
