# Start with the official Piston base image
FROM ghcr.io/engineer-man/piston:latest

# 1. Fix Debian repo links and install git
RUN echo "deb http://archive.debian.org/debian buster main" > /etc/apt/sources.list && \
    echo "Acquire::Check-Valid-Until false;" > /etc/apt/apt.conf.d/10-nocheckvalid && \
    apt-get update && apt-get install -y git

# 2. Clone Piston into a dedicated source folder
RUN git clone https://github.com/engineer-man/piston.git /piston-src

# 3. Install NPM dependencies for both the API and the CLI
RUN cd /piston-src/api && npm install && \
    cd /piston-src/cli && npm install

# 4. Create required directories, start API, install languages, and BACK THEM UP!
RUN mkdir -p /piston/packages /piston/jobs && \
    (cd /piston-src/api && node src/index.js &) && \
    sleep 15 && \
    cd /piston-src/cli && \
    node index.js ppman install python javascript typescript java php bash && \
    cp -r /piston/packages /piston-packages-backup

# 5. Set working directory to the API
WORKDIR /piston-src/api

# 6. On Render Startup: Restore the languages from the secret backup, then boot the API!
CMD ["sh", "-c", "mkdir -p /piston/packages /piston/jobs && cp -rn /piston-packages-backup/* /piston/packages/ 2>/dev/null || true && node src/index.js"]

EXPOSE 2000
