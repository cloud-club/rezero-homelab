1. 홈서버용 미니 PC ubuntu 설치
2. 홈서버에 tailscale 설치하고 tailscale login

```bash
sudo apt update
sudo apt install curl
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

1. 로컬 노트북에도 tailscale 설치 & 실행

```bash
tailscale up --ssh --accept-routes
```

1. ssh 로그인

```bash
ssh <user>@<tailscale-ip>
```

![image.png](https://github.com/user-attachments/assets/62340c91-0cda-413c-97d0-bad6ac29aa6a)

SSH 접속



- docker 설치

```bash
curl https://get.docker.com | sh 
```

- docker로 nginx 띄우기

```bash
sudo usermod -aG docker $USER
newgrp docker
docker run -d -p 2327:80 --name nginx nginx:latest
```

![image.png](https://github.com/user-attachments/assets/4cb57d7a-1548-4b3d-8e76-d5f7dbb16d0b)

- 외부에서 접속하려면?

![image.png](https://github.com/user-attachments/assets/705000c2-1f0e-4028-800f-4881e3f32372)

`tailscale 이름` : `port` 로 접근 가능하다

→ 왜?

⇒ tailscale dns에 등록이 되었기 때문
