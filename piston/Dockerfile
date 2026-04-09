FROM ghcr.io/engineer-man/piston:latest

# Disable sandbox for compatibility with Render's free tier
ENV PISTON_DISABLE_SANDBOX=true

# Pre-install languages during the build phase
RUN piston pkg install python=3.10.0 node=18.15.0 -y

# Render uses port 2000 for Piston by default
EXPOSE 2000

CMD ["node", "src/index.js"]
