```
docker pull registry.cn-hangzhou.aliyuncs.com/acs-sample/gitlab-sameersbn
docker pull registry.cn-hangzhou.aliyuncs.com/acs-sample/postgresql-sameersbn
docker pull registry.cn-hangzhou.aliyuncs.com/acs-sample/redis-sameersbn

docker tag registry.cn-hangzhou.aliyuncs.com/acs-sample/gitlab-sameersbn:latest gitlab
docker tag registry.cn-hangzhou.aliyuncs.com/acs-sample/redis-sameersbn redis
docker tag registry.cn-hangzhou.aliyuncs.com/acs-sample/postgresql-sameersbn postgresql
```
```
mkdir -p /srv/docker/gitlab/postgresql
mkdir -p /srv/docker/gitlab/redis
mkdir -p /srv/docker/gitlab/gitlab
```
``` shell
docker run --name gitlab-postgresql -d \
    --env 'DB_NAME=gitlabhq_production' \
    --env 'DB_USER=gitlab' --env 'DB_PASS=password' \
    --env 'DB_EXTENSION=pg_trgm' \
    --volume /srv/docker/gitlab/postgresql:/var/lib/postgresql \
    postgresql:latest

docker run --name gitlab-redis -d \
    --volume /srv/docker/gitlab/redis:/var/lib/redis \
    redis:latest
    
docker run --name gitlab -d \
    --link gitlab-postgresql:postgresql --link gitlab-redis:redisio \
    --publish 10022:22 --publish 10080:80 \
    --env 'GITLAB_PORT=10080' --env 'GITLAB_SSH_PORT=10022' \
    --env 'GITLAB_SECRETS_DB_KEY_BASE=long-and-random-alpha-numeric-string' \
    --env 'GITLAB_SECRETS_SECRET_KEY_BASE=long-and-random-alpha-numeric-string' \
    --env 'GITLAB_SECRETS_OTP_KEY_BASE=long-and-random-alpha-numeric-string' \
    --volume /srv/docker/gitlab/gitlab:/home/git/data \
    gitlab:latest
```
