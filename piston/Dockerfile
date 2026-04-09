FROM ghcr.io/engineer-man/piston:latest

# Essential for cloud hosting compatibility
ENV PISTON_DISABLE_SANDBOX=true

# Use port 2000 for Piston
EXPOSE 2000

# Start the API without pre-installing (we will do it via API later)
CMD ["node", "src/index.js"]
