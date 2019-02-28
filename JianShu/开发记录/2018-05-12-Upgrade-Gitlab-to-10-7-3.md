```
mkdir -p /srv/docker/gitlab10/postgresql
mkdir -p /srv/docker/gitlab10/redis
mkdir -p /srv/docker/gitlab10/gitlab/config
mkdir -p /srv/docker/gitlab10/gitlab/logs
mkdir -p /srv/docker/gitlab10/gitlab/data

docker run --name gitlab-postgresql10 -d \
    --env 'DB_NAME=gitlabhq_production' \
    --env 'DB_USER=gitlab' --env 'DB_PASS=password' \
    --env 'DB_EXTENSION=pg_trgm' \
    --volume /srv/docker/gitlab10/postgresql:/var/lib/postgresql \
    docker.io/postgres:10.3

docker run --name gitlab-redis4 -d \
    --volume /srv/docker/gitlab10/redis:/var/lib/redis \
    docker.io/redis:4.0.9

sudo docker run --detach \
    --hostname 10.61.65.67 \
    --publish 7443:443 --publish 7080:80 --publish 7022:22 \
    --name gitlab10 \
    --restart always \
    --volume /srv/docker/gitlab10/gitlab/config:/etc/gitlab \
    --volume /srv/docker/gitlab10/gitlab/logs:/var/log/gitlab \
    --volume /srv/docker/gitlab10/gitlab/data:/var/opt/gitlab \
    docker.io/gitlab/gitlab-ce:10.7.3-ce.0
```
