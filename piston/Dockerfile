# 1. Start with the official Piston image
FROM ghcr.io/engineer-man/piston:latest

# 2. Pre-install all your languages during the build phase!
# This bakes them directly into the container so they survive Render's restarts.
RUN /piston/cli/index.js ppman install python javascript typescript cpp c csharp java go rust ruby php bash

# 3. Expose the port Piston runs on
EXPOSE 2000
