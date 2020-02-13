# devops03
ITEA Devops Course

$$('body').count().then(() => { debugger});


Selenoid
./cm selenoid start -l 10 -conf ./browsers.json —vnc
Copy videos from remote server
scp -r root@192.168.243.23:/root/.aerokube/selenoid/video/ ~/video

GitLab Runner Location
/home/gitlab-runner/builds/b1db1d6b

lscpu - check parameters of machime
free -m
check folder size
du -hd1 ./.aerokube/selenoid/
delete files 
shopt -s extglob
# rm -v -f !(*.mp4)
Setup cron jobs
crontab -l
crontab -e
@midhight root command
at 07:00


Delete w/o xargs
find /root/.aerokube/selenoid/video/ -mindepth 1 -maxdepth 1 -mmin +120 -name ‘*.mp4' -delete
DOCKER
docker login -u admin -p admin123 artifactory.evaluate-it.cloud

volumes:
"volumes": ["/home/gitlab-runner/builds/captn/xlsx_data:/home/selenium/xlsx_data", "/home/gitlab-runner/builds/captn/Downloads:/home/selenium/xlsx_data/Downloads"]

from project script 
-v /home/gitlab-runner/builds/captn/xlsx_data:/usr/captn/xlsx_data:rw

docker run --rm -v /var/run/docker.sock:/var/run/docker.sock  \
    -v ${HOME}:/root                                            \
    -e OVERRIDE_HOME=${HOME}                                    \
    aerokube/cm:latest-release selenoid start --vnc --tmpfs 128

docker run --rm -v /var/run/docker.sock:/var/run/docker.sock  \
    -v ${HOME}:/root                                            \
    -e OVERRIDE_HOME=${HOME}                                    \
    aerokube/cm:latest-release selenoid start --vnc --tmpfs 128

VOLUME ["/home/gitlab-runner/builds/Downloads:/usr/captn/Downloads:z"]


Docker

docker info
docker —version

acount for captn 
artifactory.evaluate-it.cloud
admin
admin123



docker-compose up --scale nodechrome=4 -d
history
docker run --net=host automation-node node --max_old_space_size=4096 node_modules/protractor/built/cli.js conf.js --suite=full

docker run -t --shm-size 2g --net=host -v /Users/druda/WebstormProjects/CAP-N-QA-UIT:/usr/src/captn  automation-node node --max_old_space_size=4096 node_modules/protractor/built/cli.js conf.js --spec specs/other_specs/quantity_spec.js

docker run -t --shm-size 2g --net=host -v /Users/druda/WebstormProjects/CAP-N-QA-UIT:/usr/src/captn  automationwithport  node --max_old_space_size=4096 node_modules/protractor/built/cli.js conf.js --specs specs/other_specs/quantity_spec.js

Проверить маунты контейнера
docker inspect -f "{{ .Mounts }}" 27260eb9ca26

Подключиться к контейнеру
docker exec -t -i f2d67375991a /bin/bash

Right for directory for user:
#getfacl /shares/project1/reports # Check the default ACL settings for the directory 
# setfacl -m user:tecmint:rw /shares/project1/reports # Give rw access to user tecmint 
# getfacl /shares/project1/reports # Check new ACL settings for the directory

--shm-size=“"

/dev/shm:/dev/shm
--shm-size 2g
-v $(pwd):/protractor
—privileged
--net=host 
-eSCREEN_RES=1920x1080x24
FROM automation-node
COPY . .
WORKDIR .
RUN ls
RUN chmod +x run.sh
ENTRYPOINT ["./run.sh"]
CMD []


ARG DOCKER_ART_REGISTRY=artifactory.evaluate-it.cloud
ARG CI_COMMIT_SHA=${CI_COMMIT_SHA}
RUN echo $CI_COMMIT_SHA
ARG AUTOMATION_NODE=$DOCKER_ART_REGISTRY/docker/automation/automation-node-$CI_COMMIT_SHA
RUN echo $AUTOMATION_NODE
FROM $AUTOMATION_NODE
COPY . .
WORKDIR .
RUN ls

