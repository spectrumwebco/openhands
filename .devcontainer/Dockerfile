# Start with the runtime image
FROM docker.all-hands.dev/all-hands-ai/runtime:0.17-nikolaik as runtime

# Use the OpenHands image as the main image
FROM docker.all-hands.dev/all-hands-ai/openhands:0.17

# Install additional development tools
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    vim \
    && rm -rf /var/lib/apt/lists/*

# Copy runtime from the runtime image (if needed)
COPY --from=runtime / /runtime

# Set environment variables
ENV SANDBOX_RUNTIME_CONTAINER_IMAGE=docker.all-hands.dev/all-hands-ai/runtime:0.17-nikolaik \
    LOG_ALL_EVENTS=true

# Expose the port
EXPOSE 3000

# Set working directory
WORKDIR /workspace

# Start OpenHands (using the original command's structure)
CMD ["node", "dist/index.js"]