FROM ui-node:latest

RUN apt-get update \
    && apt-get install -y git
ADD id_rsa /root/.ssh/id_rsa

ENTRYPOINT ["tail", "-f", "/dev/null"]