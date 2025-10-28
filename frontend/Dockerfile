# Base image with Node and Java (for Android build)
FROM openjdk:17-jdk-slim

# Install dependencies
RUN apt-get update && apt-get install -y curl unzip git && \
    curl -sL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g yarn && \
    apt-get clean

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json yarn.lock ./
RUN yarn install --frozen-lockfile

# Copy source code
COPY . .

# Default command (you can change it to build your Android APK)
CMD ["yarn", "android"]
