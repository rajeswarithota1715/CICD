FROM : To pull the basic image

RUN:  To execute commands

CMD: To provide defaults for an executing container

ENTRYPOINT: to configure a container that will run as a executable 

The difference between CMD and ENTRYPOINT is , we can overwrite CMD and we can't overwrite ENTRYPOINT

WORKDIR: to set the working directory ,likr cd in linux

COPY: To copy a directory from local machine to the docker container  

ADD: to copy files and folders from local machine to docker containers 

EXPOSE: informs docker that the container listens on the specified network ports at run time

ENV: to set the environment variables
