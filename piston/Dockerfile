
FROM ghcr.io/engineer-man/piston:latest
RUN apt-get update && apt-get install -y git

RUN git clone https://github.com/engineer-man/piston.git /tmp/piston-repo && \
    cd /tmp/piston-repo/cli && \
    npm install

RUN (npm start &) && \
    sleep 10 && \
    cd /tmp/piston-repo/cli && \
    node index.js ppman install python javascript typescript cpp c csharp java go rust ruby php bash

EXPOSE 2000
