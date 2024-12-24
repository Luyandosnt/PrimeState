# Use a base image with Ubuntu for compatibility
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Update the package manager and install basic tools
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    xz-utils \
    libglu1-mesa \
    lib32stdc++6 \
    && apt-get clean

# Clone the Flutter SDK into the container
RUN git clone https://github.com/flutter/flutter.git /usr/local/flutter

# Add Flutter to the PATH
ENV PATH="/usr/local/flutter/bin:/usr/local/flutter/bin/cache/dart-sdk/bin:${PATH}"

# Pre-cache Flutter binaries (optional but speeds up setup)
RUN flutter precache

# Run Flutter doctor to ensure all dependencies are downloaded
RUN flutter doctor --android-licenses || true && flutter doctor