# Docker 安装容器

Docker install container

------

## Portainer

```bash
docker search portainer #搜索容器
docker pull portainer/portainer #拉取容器

docker volume create portainer_data
docker run -d -p 9000:9000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```

