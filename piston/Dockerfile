# Start with the official Piston base image
FROM ghcr.io/engineer-man/piston:latest

# 1. Install git so we can grab the official Piston CLI tool
RUN apt-get update && apt-get install -y git

# 2. Clone the Piston repository to get the CLI tool, and install its dependencies
RUN git clone https://github.com/engineer-man/piston.git /tmp/piston-repo && \
    cd /tmp/piston-repo/cli && \
    npm install

# 3. Start the Piston API in the background, wait 10 seconds for it to boot, then install the languages!
RUN (npm start &) && \
    sleep 10 && \
    cd /tmp/piston-repo/cli && \
    node index.js ppman install python javascript typescript cpp c csharp java go rust ruby php bash

# 4. Expose the port
EXPOSE 2000
