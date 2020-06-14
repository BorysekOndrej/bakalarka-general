FROM ubuntu:18.04

MAINTAINER Ondrej Borysek "bakalarka@borysek.net"

RUN apt-get update -y && \
    apt-get install -y python3.7 python3.7-dev python3-pip git

RUN git clone https://github.com/BorysekOndrej/bakalarka3.git /app/bakalarka3
RUN cd /app/bakalarka3 && git checkout integration
RUN cd /app/bakalarka3 && mkdir db tmp log

WORKDIR /app/bakalarka3

RUN python3.7 -m pip install -r requirements.txt

# https://stackoverflow.com/a/39278224
# The following is used to invalidate caching when branch changes and then only doing changes.
ADD https://api.github.com/repos/BorysekOndrej/bakalarka3/git/refs/heads/integration branch_version.json
RUN cd /app/bakalarka3 && git checkout integration && git pull
RUN python3.7 -m pip install -r requirements.txt

# 
# COPY . /app
# 
ENTRYPOINT [ "rq", "worker", "sslyze-tasks", "--url", "redis://redis"]
# ENTRYPOINT [ "/bin/bash"]
# 
# CMD [ "app.py" ]
