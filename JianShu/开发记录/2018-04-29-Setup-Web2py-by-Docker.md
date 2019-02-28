```
docker pull registry.cn-hangzhou.aliyuncs.com/frameyl/web2py
docker tag registry.cn-hangzhou.aliyuncs.com/frameyl/web2py web2py

sudo mkdir -p /srv/docker/web2py/applications/
sudo mkdir -p /srv/docker/web2py/log/

docker run -d \
  -e WEB2PY_ADMIN=spirent \
  -i -t \
  -p 9080:80 -p 9443:443 \
  -v /srv/docker/web2py/applications:/opt/web2py/applications \
  -v /srv/docker/web2py/log:/var/log/nginx \
  --name web2py \
  registry.cn-hangzhou.aliyuncs.com/frameyl/web2py:2.16.1

git pull origin master
sudo rm -rf /srv/docker/web2py/applications/RegressionReport
sudo cp -R RegressionReport/ /srv/docker/web2py/applications/
sudo chown `stat -c "%u:%g" /srv/docker/web2py/applications` -R /srv/docker/web2py/applications/RegressionReport

docker exec -i -t web2py /bin/bash
```
