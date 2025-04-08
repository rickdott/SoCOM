# Base image found at https://hub.docker.com/r/pytorch/pytorch/tags
FROM pytorch/pytorch:2.5.1-cuda12.1-cudnn9-devel

# Install git and jupyter, git is not necessary for this barebones install but may be needed to pull other repositories
RUN apt-get update && apt-get install -y git \
    && pip install jupyter

RUN apt install cifs-utils -y

# Upgrade pip
WORKDIR /tmp
RUN python -m pip install --upgrade pip

# Requirements.txt must be in the same folder as this dockerfile, contains the packages
# TODO: Automatically pull requirements from github package?
COPY ./SoCOM/docker/requirements.txt .
RUN python -m pip install -r requirements.txt

WORKDIR /workspace

COPY ./hmp-ai /workspace/hmp-ai
RUN python -m pip install -e /workspace/hmp-ai/src

# Uncomment this if you want to use a custom version of hmp
COPY ./hmp /workspace/hmp
RUN python -m pip install -e /workspace/hmp

COPY ./SoCOM/docker/pyrightconfig.json /workspace
# Mounting must be done with added capabilities that are only available after running the dockerfile, so start by running a script that contains that info
COPY ./SoCOM/docker/mount_drive.sh /tmp/mount_drive.sh
RUN chmod +rwx /tmp/mount_drive.sh
RUN mkdir /workspace/data
ENTRYPOINT /tmp/mount_drive.sh 
#ENTRYPOINT ["tail", "-f", "/dev/null"]
