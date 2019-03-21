FROM ubuntu:xenial AS base
RUN apt-get update && \
    apt-get install -y --no-install-recommends software-properties-common gdb && \
    apt-get install -y --no-install-recommends cmake gcc g++ make && \
    rm -rf /var/lib/apt/lists/*

FROM base AS build-env
RUN apt-get update && \
    apt-get install -y libcurl4-openssl-dev && \
    rm -rf /var/lib/apt/lists/* 
WORKDIR /app
COPY . ./
RUN cmake -DCMAKE_BUILD_TYPE=Debug . 
RUN make

FROM base AS ssh-env
RUN apt-get update && apt-get install -y --no-install-recommends openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:screencast' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile
EXPOSE 22

FROM ssh-env
WORKDIR /app
COPY --from=build-env /app ./
CMD service ssh start && ./postsvr
