# 在 Ubuntu 上安装 Docker （二进制文件形式安装）



1. **下载docker的二进制文件**
    binary 下载地址：[Docker 二进制文件](https://download.docker.com/linux/static/stable/)
    ```bash
    # 在写这个文档时, docker的版本为27.3.1
    sudo tar xzvf docker-27.3.1.tgz
    sudo cp docker/* /usr/bin/
    ```

2. **创建 Docker 用户组**
    ```bash
    sudo groupadd docker
    sudo usermod -aG docker $USER
    sudo newgrp docker
    ```

3. **使用systemd管理docker**
    文件在仓库的systemd目录下
    ```bash
    sudo cp docker.service /etc/systemd/system/
    sudo cp containerd.service /etc/systemd/system/
    sudo cp docker.socket  /usr/lib/systemd/system/docker.socket
    ```

4. **启动docker**
    ```bash
    systemctl daemon-reload
    systemctl start containerd
    systemctl start docker
    ```
5. **设置开机自启动**
    ```bash
    systemctl enable containerd
    systemctl enable docker
    systemctl enable docker.socket
    ```

2. **安装 Docker Compose**
    ```bash
    # 从github下载,截止当前docker-compose 的版本是v2.31.0
    wget https://github.com/docker/compose/releases/download/v2.31.0/docker-compose-linux-x86_64
    cp docker-compose-linux-x86_64 /usr/bin/docker-compose
    chmod +x /usr/bin/docker-compose
    ```

4. **验证Docker Compose 的安装**
    ```bash
    docker-compose -v
    ```
    如果看到 `docker-compose`的版本号，说明安装成功。

