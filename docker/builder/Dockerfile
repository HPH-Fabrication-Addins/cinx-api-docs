FROM slatedocs/slate

RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt install -y ruby ruby-dev build-essential libffi-dev zlib1g-dev liblzma-dev nodejs patch
RUN apt install -y bundler
RUN apt install -y git

COPY ./gitconfig /root/.gitconfig

