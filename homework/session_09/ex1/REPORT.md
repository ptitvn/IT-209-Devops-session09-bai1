# BÁO CÁO THỰC HÀNH: BÀI 1
## Kiểm tra cài đặt Docker Engine và chạy Container Hello-World

---

### 1. Thông tin chung
- **Bài tập:** Bài 1: Kiểm tra cài đặt Docker Engine và chạy Container Hello-World
- **Mục tiêu:** Thực hành chạy các lệnh kiểm tra phiên bản Docker CLI và khởi chạy container đầu tiên trên máy cá nhân.
- **Môi trường thực thi:**
  - OS: Windows 11 / WSL2 Linux Kernel 6.18.33.2-microsoft-standard-WSL2
  - Docker Desktop: 4.92.0
  - Docker Engine / CLI Version: 29.8.0 (API version 1.56)
  - Phân quyền: Docker CLI kết nối trực tiếp tới Docker Daemon mà không cần gõ tiền tố `sudo` (trên Linux nếu gặp lỗi phân quyền có thể dùng lệnh `sudo usermod -aG docker $USER && newgrp docker`).

---

### 2. Kết quả thực thi các lệnh CLI cơ bản

#### Lệnh 1: `docker version`
```bash
$ docker version
Client:
 Version:           29.8.0
 API version:       1.56
 Go version:        go1.26.8
 Git commit:        88096ef
 Built:             Thu Sep  3 21:53:38 2026
 OS/Arch:           windows/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.92.0 (240144)
 Engine:
  Version:          29.8.0
  API version:      1.56 (minimum version 1.40)
  Go version:       go1.26.8
  Git commit:       3ce5872
  Built:            Thu Sep  3 21:51:20 2026
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          v2.3.5
  GitCommit:        1294c24a7da8e5a793ed378161673abe94118892
 runc:
  Version:          1.5.1
  GitCommit:        v1.5.1-0-g8f2685a4
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

#### Lệnh 2: `docker info`
```bash
$ docker info
Client:
 Version:    29.8.0
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.140.0
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.31.0
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.37.1
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.5.1
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.0.47
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  v0.4.4
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-desktop.exe
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.7
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-dhi.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.31
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.0
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.43.3
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.6
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-model.exe
  offload: Docker Offload (Docker Inc.)
    Version:  v0.6.27
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-offload.exe
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.2.2
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-pass.exe
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-sandbox.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.24.0
    Path:     C:\Users\LE DONG\.docker\cli-plugins\docker-scout.exe

Server:
 Containers: 2
  Running: 1
  Paused: 0
  Stopped: 1
 Images: 3
 Server Version: 29.8.0
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 1294c24a7da8e5a793ed378161673abe94118892
 runc version: v1.5.1-0-g8f2685a4
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.33.2-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 12
 Total Memory: 11.54GiB
 Name: docker-desktop
 ID: 32c45b9c-6251-4436-9ec0-b6ba15bf115d
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables
```

#### Lệnh 3: `docker run hello-world`
```bash
$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

---

### 3. Kiểm tra và Đánh giá kết quả

| Tiêu chí | Yêu cầu | Kết quả thực tế | Trạng thái |
|---|---|---|---|
| Kết nối Docker Daemon | Không cần sudo, kết nối thành công | Client & Server giao tiếp thông suốt | **ĐẠT (PASSED)** |
| Phiên bản Docker CLI (`docker version`) | Hiển thị thông tin client và server | Client: 29.8.0, Server: 29.8.0 | **ĐẠT (PASSED)** |
| Trạng thái hệ thống (`docker info`) | Hiển thị thông tin cấu hình Docker Engine | Hiển thị chi tiết Server & Client Engine | **ĐẠT (PASSED)** |
| Khởi chạy Container (`docker run hello-world`) | Xuất hiện thông điệp "Hello from Docker!" | Hiển thị chuẩn xác đầy đủ thông điệp | **ĐẠT (PASSED)** |

---

### 4. Kết luận
- Quá trình cài đặt và cấu hình Docker Engine trên máy cá nhân hoạt động bình thường, không gặp lỗi phân quyền.
- Docker Client và Docker Daemon kết nối ổn định.
- Đã pull và chạy thành công image `hello-world`.
