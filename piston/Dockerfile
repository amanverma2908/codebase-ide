FROM ghcr.io/engineer-man/piston:latest

# Disable sandbox for compatibility with Render
ENV PISTON_DISABLE_SANDBOX=true

# Explicitly create the directories Piston expects to exist
RUN mkdir -p /piston /piston/packages /piston/jobs

# Render uses port 2000 for Piston by default
EXPOSE 2000

# Notice we removed the CMD ["node", "src/index.js"] line here.
# We are letting the official Piston image use its own default startup command.
