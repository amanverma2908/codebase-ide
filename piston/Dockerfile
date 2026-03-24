# Start with the official Piston base image
FROM ghcr.io/engineer-man/piston:latest

# 1. Fix the Debian archive links (Buster is End-of-Life) so we can install git
RUN echo "deb http://archive.debian.org/debian buster main" > /etc/apt/sources.list && \
    echo "Acquire::Check-Valid-Until false;" > /etc/apt/apt.conf.d/10-nocheckvalid && \
    apt-get update && apt-get install -y git

# 2. Clone the Piston repository to get the CLI tool
RUN git clone https://github.com/engineer-man/piston.git /tmp/piston-repo && \
    cd /tmp/piston-repo/cli && \
    npm install

# 3. Start the Piston API in the background, wait 10 seconds for it to boot, then install the languages!
RUN (npm start &) && \
    sleep 10 && \
    cd /tmp/piston-repo/cli && \
    node index.js ppman install python javascript typescript cpp c csharp java go rust ruby php bash


EXPOSE 2000
